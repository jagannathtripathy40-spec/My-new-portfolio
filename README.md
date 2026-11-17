import random

def play_cricket():
    print("=== CRICKET GAME MEIN AAPKA SWAGAT HAI ===")
    user_score = 0
    wickets = 0
    max_balls = 6  # 1 over ka match

    print(f"\nAapki batting shuru hoti hai! (Total balls: {max_balls})")
    
    for ball in range(1, max_balls + 1):
        try:
            user_run = int(input(f"Ball {ball}: 1 se 6 ke beech mein koi number chuniye: "))
            if user_run < 1 or user_run > 6:
                print("Kripya 1 se 6 ke beech ka hi number dalein.")
                continue
        except ValueError:
            print("Kripya sahi number dalein!")
            continue

        comp_run = random.randint(1, 6)
        print(f"Computer ne dala: {comp_run}")

        if user_run == comp_run:
            print("OUT! Aap out ho gaye hain!")
            break
        else:
            user_score += user_run
            print(f"Aapko mile {user_run} runs. Total Score: {user_score}\n")

    print("\n--- INNINGS SAMAPT ---")
    print(f"Aapka Final Score: {user_score} runs")

if __name__ == "__main__":
    play_cricket()
