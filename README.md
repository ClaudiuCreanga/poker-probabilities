you have 10 possible sequences of cards (ace can be 11 and 15)
you have 13 cards in a colour
```
import math
def combinations(n,k):
    all_posibilities = float(math.factorial(n) / (math.factorial(k) * math.factorial(n - k)))
    return all_posibilities

def calculate_probability(frequency):
    all_posibilities = combinations(52,5)
    return (frequency / all_posibilities) * 100

def poker_probabilities():

    royal_flush_frequency = combinations(4,1)
    royal_flush_probability = calculate_probability(royal_flush_frequency)

    straight_flush_frequency = combinations(4,1) * combinations(9,1)
    straight_flush_probability = calculate_probability(straight_flush_frequency)

    four_of_a_kind_frequency = combinations(13,1) * combinations(13-1,1) * combinations(4,1) # 13 cards, 12 possibilities for the fifth one and 4 colors
    four_of_a_kind_probability = calculate_probability(four_of_a_kind_frequency)

    full_house_frequency = combinations(13,1) * combinations(4,3) * combinations(13-1,1) * combinations(4,2) # first three: 13 cards, 4 posibilities, last two: 12 cards, 6 posibilities
    full_house_probability = calculate_probability(full_house_frequency)

    flush_frequency = (combinations(13,5) * combinations(4,1) - royal_flush_frequency - straight_flush_frequency)
    flush = calculate_probability(flush_frequency)

    straight_frequency = combinations(10,1) * 4**5 - straight_flush_frequency # 10 possible sequences, 4 choices from all colours
    straight_probability = calculate_probability(straight_frequency)

    three_of_a_kind_frequency = combinations(13,1) * combinations(4,3) * combinations(13-1,2) * 4**2 # 13 cards, 4 posibilities, choose 2 from 12 cards,
    three_of_a_kind_probability = calculate_probability(three_of_a_kind_frequency)

    two_pair_frequency = combinations(13,2) * combinations(4,2)**2 * combinations(13-2,1) * combinations(4,1) # 2 pairs and the fifth card not from a pair
    two_pair_probability = calculate_probability(two_pair_frequency)

    one_pair_frequency = combinations(13,1) * combinations(4,2) * combinations(13-1,3)* combinations(4,1)**3 # 1 pair and three random cards without the one in the pair
    one_pair_probability = calculate_probability(one_pair_frequency)

    no_pair_frequency = (combinations(13,5) - 10) * (combinations(4,1)**5-4) # no pair
    no_pair_probability = calculate_probability(no_pair_frequency)

    print(royal_flush_probability)

poker_probabilities()
```

