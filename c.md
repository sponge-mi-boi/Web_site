﻿# 1
Probability theory is built from set theory just like how statistics is built from probability theory.
The set S of all possible outcomes of an experiment is called the sample space of the given experiment. For tossing a coin, $S = \{H,T\}$ would be the sample space. Usually, only countable sample spaces should exist because it is physically not possible really, or obviously, to have an uncountable number of measurements, but this approximation is very accurate and makes the description easier.
An event is any collection of possible outcomes of an experiment, meaning any subset of S. Event A occurs if the outcome of the experiment is in the set A, a subset of S.
The property of containment: $A \subset B \Leftrightarrow x \in A \Rightarrow x \in B$
The property of equality: $A = B \Leftrightarrow A \subset B$ and $ B \subset A$
Union: $A \cup B = \{x: x \in A$ or $x \in B \}$
Intersection: $A \cap B = \{x: x \in A ,$ and $\ x \in B \}$
Complementation: $A^c = \{x:x \notin A \}$
ex) $S = \{1,2,3,4\}$. Events possible are $A = \{1,4\}$ and $B=\{2,3,4\}$. Then, $A \cup B = S, A \cap B = \{4\}, A^c = \{2,3\}$. Also, $(A \cup B) ^c = \not 0$, where $\not 0$ is the empty set, or the set with no elements.
These elementary set operations have the properties of commutativity, associativity, distributivity, and satisfy DeMorgan's Laws.
An example is the proof of the first law in the last one, DeMorgan's Laws.
Proof: $x \in (A \cup B)^c \Rightarrow x \in A^c \cap B^c$ will be proved first. $x \in (A \cup B)^c$ means $x \notin A$ and $\ x \notin B$ which means $x \in A^c$ and $x \in B^c$. Similarly, $x \in A^c$ and $x \in B^c$ means $x \notin A$ and $x \notin B$, means $x \in (A \cup B)^c$, meaning $x$ is neither in $A$ nor in $B$. Therefore, $(A \cup B)^c = A^c \cap B^c$.
Similar proofs follow for the rest of the properties.
This concept can be extended to infinite collections such $\cup_{i=1}^{\inf} A_i = \{ x \in S : x \in A_i$ for some $i\}$ for an infinite union and $\cap_{i=1}^{\inf} A_i = \{ x \in S : x \in A_i$ for all $i\}$.
ex) if $S = (0,1]$ and $A_i = [(\frac{1}{i}),1]$ for some $i$, then $\cup_{i=1}^\inf A_i = \cup_{i=1}^\inf [(\frac{1}{i}),1] = (0,1]$. Note here the $[$ means that the set includes the given boundary point and $($ means it does not. Then, $\cap_{i=1}^\inf A_i = \cap_{i=1}^\inf [(\frac{1}{i}),1] = \{1\}$.
If the indices, meaning the set being used to describe the index of the elements of the index set, is uncountable, then unions and intersections for uncountable sets are easily defined. These are not important in probability.
Two events A and B are disjoint, or mutually exclusive, if $A \cap B = \not 0$. The set of events $\{A_i\}_i$ are mutually exclusive if $A_i \cup A_j = \not 0$ for all $\ i \neq j$. They have no elements in common.
ex) $\{A_i\}_i$ such $A_i =[i,i+1)$ for $i \in \mathcal N$, (0,1,2...), is a collection of pairwise disjoint sets, meaning $\cup_{i=0}^\inf A_i = [0,\inf)$.
If $\{A_i\}_i$ is mutually exclusive and $\cup_{i=0}^\inf A_i = S$, then the collection $\{A_i\}_i$ is said to form a partition of $S$.
The axiomatic foundations of prob thy need to be studied
A collection of subsets of S is called a sigma algebra, or (Borel field), and is denoted by B if it satisfies
a) $\not 0 \in B$ meaning the empty set is an element of B
b) If $A \in B$, then $A^c \in B$, meaning that B is closed under complementation
c) If $\{A_i\}_i \in B$, then $\cup_{i=1}^\inf A_i \in B$ meaning that B is closed under countable unions.
A sigma algebra therefore always contains $S$, the set itself too, since for every sigma algebra, $\not 0 \in B \Rightarrow \not 0^c = S \in B$ from the first and second properties.
Also by De Morgan's laws, $\cup_{i=1}^\inf A_i \in B \Rightarrow (\cup_{i=1}^\inf A_i)^c = \cap_{i=1}^\inf A^c_i \in B$ and the replacement $A_i^c \Rightarrow A_i$ can be made since if $A_i \in B$, then $A_i^c \in B$ too. Therefore, $\cap_{i=1}^\inf A_i \in B$ meaning B is closed under countable intersections as well
A space S can have many different sigma algebras. The trivial sigma algebra is the collection of sets $B = \{\not 0, S\}$ where the properties are trivially shown to be satisfied.
The most important example is the sigma algebra-I, which is defined for a countable set S as the collection of all subsets of S, meaning $B = P(S)$, where $P$ indicates the power set. The length, or cardinality, of the power set is merely, given the set is of size n, $2^n$, since every element in B can be chosen to be either included or excluded from a given set independently
ex) $\S = \{a,b,c\}$, then $B = \{\{a\},\{b\},\{c\},\{a,b\},\{a,c\},\{b,c\},\not 0, S\}$
The sigma algebra-II is given that $S = (-\inf,\inf)$, all sets of the form $[a,b],(a,b],[a,b),(a,b)$, for all  $a,b \in \mathcal R$
This leads to the definition of a probability function: Given a sample space S and an associated sigma algebra B, a probability function is a function denoted P with domain B such that
$P(A)\geq 0$ for all $A \in B$
$P(S) = 1$
If $\{A_i\}_i \in B$ are mutually exclusive, then $P(\cup_{i=1}^\inf A_i) = \sum_{i=1}^\inf P(A_i)$
These are called the Kolmogorov Axioms and define a probability function. There can be several of these associated with a given sample set.
ex) The tossing of a fair coin has the sample space $S= \{H,T\}$. The definition of fair implies that $P(\{H\}) = P(\{T\})$ and $P(S) = P(\{H\} \cup \{T\}) = P(\{H\}) + P(\{T\})$ by axioms 2 and 3. Therefore, $2P(\{H\}) = 1 \Rightarrow  P(\{H\}) = P(\{T\} )= \frac{1}{2}$
To define a probability function in a general manner $\,S = \{s_1,...,s_n\}$ be a finite set and B be any sigma algebra of the subsets of that. Let $p_i$ be nonnegative numbers that sum to * For any $A \in B$, define $P(A) = \sum_{\{i,s_i \in A\} } p_i$, P is a probability function on B. This is true for even a countable set.
ex) A dart board with radius $r$ and each ring is of width $r/5$ meaning that if the assumption is the board is always hit then $P(i) =$ Area of region i / Area of dart board, meaning for example $P(1) = (\pi r^2 * \pi (4r/5)^2)/ \pi r^2 = 1 * (4/5)^2$ which should for all 5 regions sum to 1, meaning it is a probability distribution.
Theorem: If P is a probability function and A is any set in B,
$P(\not 0) = 0$
$P(A) \leq 1$
$P(A^c) = 1 - P(A)$
Proof: For the last one $P(S) = P(A \cup A^c) = 1$ by the 2nd axiom, meaning then by the 3rd axiom $P(A \cup A^c) = P(A) + P(A^c)$, leading to $P(A^c) = 1 - P(A)$. $P(A^c) \geq 0 \Rightarrow P(A) \leq 1$. For the first statement $P(S) = P(S \cup \not 0) = 1 \Rightarrow P(S) + P(\not 0) = 1 + P(\not 0) = 1 \Rightarrow P(\not 0 ) = 0$
Theorem: If P is a probability function and A and B are any sets in B,
$P(B \cap A^c) = P(B) * P(A \cap B)$
$P(A \cup B) = P(A) + P(B) * P(A \cap B)$
If $A \subset B$, then $P(A) \leq P(B)$
Proof: For the first statement, note that $B = \{B \cap A\} \cup \{B \cap A^c\}$, meaning since this is a partition of B, $P(B) = P(B \cap A)+ P(B \cap A^c) \Rightarrow P(B \cap A^c) = P(B) * P(A \cap B)$. For the second, note $A \cup B = A \cup \{ B \cap A^c \}$, meaning $P(A \cup B) = P(A) + P(B \cap A^c) = P(A) + P(B) * P(A \cap B)$ by the first statement. For the last one, $A \subset B \Rightarrow A \cap B = A \Rightarrow P(B \cap A^c) = P(B) * P(A) \geq 0$ where the first statement was used in the last step. This means that $P(A) \leq P(B)$.
A useful corollary is since $P(A \cup B) \leq 1 \Rightarrow P(A) + P(B) * P(A \cap B) \leq 1 \Rightarrow P(A \cap B) \geq P(A) + P(B) * 1$ where the second statement was used in the last step. This is known as Bonferroni's Inequality. Useful for large individual probabiliites since it gives in those situations a non negative lower bound if the intersectional probability is hard to calculate
Theorem: If P is a probability function,
$P(A) = \sum_{i=1}^\inf P(A \cap C_i)$ for any partition $\{C_i\}_i$
$P(\cup_{i=1}^\inf A_i) \leq \sum_{i=1}^\inf P(A_i)$ known as Boole's inequality
Proof: For the first, $A = A \cap S = A \cap (\cup_{i=1}^\inf C_i) = \cup_{i=1}^\inf (A \cap C_i )$ where the distributive property was used in the last step. Then, $P(A) = P(\cup_{i=1}^\inf (A \cap C_i ) ) = \sum_{i=1}^\inf P(A \cap C_i)$ since the $A \cup C_i$ are disjoint, allowing for the laws of the probability function's definition to be used. For the second, ...
Counting can become complicated, but starts simple.
The Fundamental Theorem of Counting: If a job consists of k separate tasks, the ith of which can be done in $n_i$ ways, $i \in \{1,...,k\}$, then the entire job can be done in $n_1 \times n_2 ... n_k = \Pi_{i=1}^k n_i$ ways totally.
The two important aspects of counting are if replacement is allowed and if the ordering is important.
For a positive integer n, $n! = n(n-1)...1$ with the definition $0! = 1$.
There are four unique cases of counting then to be looked
Ordered, without replacement
To pick k objects from a set of n objects $n(n-1)...(n-k) = \frac{n!}{(n-k)!}$ is the number of possibilities.
Ordered, with replacement
$n(n)...n = n^k$ possibilities
Unordered, without replacement
$n(n-1)...(n-k)/k(k-1)...1 = \frac{n!}{(n-k)! \ k \ !}$ since there are $k(k-1)...1 = k!$ ways to order $k$ objects, and these are all the same exact outcome if there is no ordering.
For example, the set $\{1,2\}$ has two ordered possibilities of being arranged $\{1,2\}, \{2,1\}$, but only one way of being arranged if order does not matter.
This is represented as $n$ choose $k$, $n \geq k$, where $\frac{n!}{k!(n-k)!}$ which is the amount of ways k objects can be chosen from n total objects in an unordered way, or if the objects are exactly identical, meaning their order does not matter.
Unordered with replacement
This is the toughest case to measure intuitively, but it can be looked at by looking at each possibility in terms of each individual replacement. There are n possibilities for the first choice, but for the second, because of unordering there are $n+1$ possibilities, not just n. This is because the 2nd object could have just as easily been chosen first, meaning the size of the sample space initially is not big enough to be the whole. In fact, for k chosen objects, there will be $n(n+1)...(n+k-1)$ total possibilities of choosing, since upon each pick, an object gets added to the overall space. Therefore, it is better to regard this situation as the choice of k objects from $n+k-1$ total objects and the $k$ objects themselves being indistinguishable makes the result to be $\frac{n(n+1)...(n+k-1)}{k!} = \frac{(n+k-1)!}{k!(n+k-1-k)!} = \frac{(n+k-1)!}{k!(n-1)!}$
Counting analysis is important in the situation of randomness, meaning that S is a finite set, and all outcomes in S are equally likely. In this situation, $S = \{s_i\}_i, i \in \{1,...,N\}$, meaning $P(\{s_i\}) = \frac{1}{N}$, leading to the fact for any given event, subset, $A$ that occurs in $S$, $P(A) = \sum_{s_i \in A} P(\{s_i\}) = \sum_{s_i \in A} \frac{1}{N} = \frac{A_N}{N}$ where $A_N$ is the number of events, or elements, in N.
ex) Consider drawing 5 cards from a deck of 52 cards, without replacement, and unordered. The number of total events, or possible draws, $\frac{52!}{5!47!} = 2598960$. The probability of having 4 aces in the hand would be the number of events, or sets, with 4 aces, which is 48 since the first 4 cards need to be aces and there are 48 possibilites for the 5th card, divided by the total number of events, meaning $P($four aces$) = \frac{48}{2598960}$. The chance of having 4 cards of the same rank would be the number of cards 13, times the number of possibilities of 5th $\frac{13*48}{2598960}$, and the chance of exactly one pair would be the number of different cards times the number of ways to choose 2 cards out of the 4 of each type which exist in deck which is unordered of course, times the number of ways to choose 3 different types of cards from the remaining 12 types of cards left times the number left of each of these types, which is just $4*4*4$. Note that type means number of the card here, and there is 4 of each num in the deck of course. Therefore, the total number of hands, or sets, with a pair $13* \binom{4}{2} \binom{12}{3}*64$, which is divided by the total number of possible events, or hands, in this space.
For sampling without replacement, the probability of an outcome is independent of whether the set is considered ordered or not. However, this is not true for sampling with replacement interestingly as can be seen from a basic example. Choosing 2 items out of 3 total items gives an unordered outcome of $\{1,2\}$ as one of the possibilities. However, if the space is considered ordered, this unordered outcome corresponds to two ordered outcomes formed of the same elements $\{1,2\},\{2,1\}$. The space of unordered events is less than the space of ordered events for a given sample space, unless there is only one event in the whole set. This is fascinating because the choice, or more accurately, information about an ordered set means that the probability assigned to the set by an observer is different compared to one who does not have that information, and considers the set as merely unordered. In the above example, the probability of $1/6$ in the unordered sample space corresponds to the probability of $2/9$ in the ordered sample space. However, if the second observer was able to distinguish two elements apart, but then chooses to consider them unordered, he would still get $2/9$ for that event since he knows the total number of events possible in this space is $9$.
Conditional probability is another huge aspect when it comes to calculations.
ex) What is the chance of 4 aces being drawn from a deck if only 4 cards are drawn? From before, $\binom{52}{4}$ is the total number of possibilities for these 4 cards, and because of unorderness, only one of these can be 4 aces, meaning the probability is 1 over that.
Another way of doing this is to use conditional probabilities and to update the sample space after every interaction with it. The probability the first card is an ace is $4/52$, the second card being an ace is $3/51$, and so on meaning $(4/52)(3/51)(2/50)(1/49)$ is the chance
If A and B are events, or subsets, in S, and $P(B) \geq 0 $, then the conditional probability of A given B is $P(A|B) = \frac{P(A \cap B)}{P(B)}$
$P(x) = P(x|B)$ is a probability function which satisfies Kolmogorov's Axioms.
ex) A,B,C one of them will be pardoned but A is told that B will be executed. If W is the event that A is told that B will die, $P(A|W) = \frac{P(A \cap W)}{P(W)}$. Then, $P(W) = P($warden says B dies$) = P($warden says B dies and A is pardoned$) + P($warden says B dies and B is pardoned)$ + P($ warden says B dies and C is pardoned$)$ since there are all the possible subsets of the given event of the warden telling A that B dies, meaning that either one of these three things have to happen. Assuming the warden is telling the truth, $P($B dies and B is pardoned)=0. However, note that the chance A or B or C gets pardoned is random as dictated by the problem, meaning that $1/3$ of each happening. Also, the warden cannot tell A whether he dies, because then A would know for sure, and there is nothing for him to calculate. That means the warden tells A that B dies, but A is pardoned or C is pardoned, or the warden tells A that C dies, but A is pardoned or B is pardoned. Therefore, P(warden says B dies and A is pardoned$) = 1/2(1/3) = 1/6$ and P( warden says B dies and C is pardoned$) = 1/3$. Therefore, $P(W) = 1/6 + 1/3 = 1/2$, and $P(A|W) =$ P(warden says B dies and A is pardoned) / P(warden says that B dies)  $= (1/6)/(1/2) = 1/3$ as expected
Theorem: Bayes' Rule
Let $A_i$ be a partition of the sample space and let B be any set. Then for each $i$, $P(A_i|B) = \frac{P(B|A_i)P(A_i)}{\sum_{j=1}^\inf P(B|A_j)P(A_j)}$
ex) Either a dot or dash is sent in Morse code with $P(A) = 3/7, P(B) = 4/7$. Say there is an interference and a dot is mistakenly received as a dash with probability $1/8$ and vice versa meaning $P(B_r|A) = 1/8$. What is the chance a dot was sent, given a dot is received? $P(A|A_r) = \frac{P(A_r|A) P(A)}{P(A_r)}$. Then, from above, it is known $P(A_r|A) = 7/8$, $P(A) = 3/7$, and $P(A_r) = P(A_r \cap A) + P(A_r \cap B) = P(A_r|A)P(A) + P(A_r|B)P(B)$ from the bottom part of Bayes' Rule meaning $P(A_r) =7/8 3/7 + 1/8 4/7 = 3/8 + 1/14 = 25/56$, meaning $P(A|A_r) = 7/8(3/7)/(25/56) = 21/25$
If B and A are independent, $P(A|B) = P(A)$. Note if this is true, $P(B|A) = \frac{P(A|B)P(B)}{P(A)} = P(A) \frac{P(B)}{P(A)} = P(B)$. Therefore, if A is independent of B, B is independent of A. Also, since $P(B|A)P(A) = P(A \cap B) \Rightarrow P(A \cap B) = P(A)P(B)$ This is taken to be the definition of statistical independence.
ex) The probability to throw at least 1 six in 4 rolls of a die would be P(1 six at least) = 1 * P(no six in the four rolls) = 1 * $(5/6)^4$ = .518 since each roll is independent and the chance of not getting a 6 in a given roll is $5/6$.
Theorem: If A and B are independent events, then the following pairs are also independent
A and $B^c$
$A^c$ and B
$A^c$ and $B^c$
Proof: For the first statement, $P(A \cup B^c) = P(A) * P(A \cup B) = P(A) * P(A)P(B) = P(A)(1-P(B)) = P(A)P(B^c)$. The others are similar.
Independence among multiple events, more 2, requires a strong condition. A collection of events $A_n$ are mutually independent if for any subcollection $A_{i_j}$, $P(\cap_{j=1}^k A_{i_j}) = \Pi_{j=1}^k P(A_{ij})$. This means for 3 events $A,B,C \rightarrow P(AB)=P(A)P(B),P(BC)=P(B)P(C),P(ABC)=P(A)P(B)P(C),P(AC)=P(A)P(C)$.
Random variables are used to reduce the size of the sample space to simplify situations. For example, tossing a coin 10 times results in a sample space of $2^{10}$.However, this situation can just be described without loss of information by how many of these coins land in heads, or its opposite, meaning a set of numbers inclusive, the integers, from 0 to 10. This is defined explicitly by an surjective mapping from the original sample space to this new one. This is the definition of a random variable, a function from the sample space S to the real numbers.
To define a probability function $P$ on this new sample space, consider a random variable $X: S \rightarrow \chi, S = \{s_i\}_i, \chi = X() = \{x_i\}_i$. The induced probability function is to merely state that $P_X(x_i) = P(\{s_j \in S: X(s_j) = x_i\})$. The probabilities of all the elements in S associated, or mapped to, an element in X are all simply added together, and those give the probability of the element in X occurring. This induced probability function can be shown to satisfy the Kolmogorov Axioms, which is not too difficult. $P_X \equiv P$, meaning just P can be used from now on to represent $P_X$.
ex) Let S be the strings of all possible 50 0s and 1s. If equally likely, and X is defined as the number of 1s, the number of strings with 27 1s merely has the probability $P(X = 27) = \binom{50}{27}/ 2^{50}$. In general, for any $i \in \chi$, $P(X = i) = \binom{50}{i}/2^{50}$
An induced probability function is defined similarly for countable sets and uncountable
The cumulative distribution function or CDF of a random variable X, for every random variable X, $F_X(x) = P_X(X \leq x)$ for all $x$.
ex)The experiment of tossing three coins, and $X$ is the number of heads, $F_X(x) = \begin{cases} 0 & \text{if  } -\inf < x < 0\\ 1/8 &  \text{if  }  0 \leq x < 1  \\ 1/2 & \text{if } 1 \leq x < 2 \\ 7/8  & \text{if } 2 \leq 3 \\ 1 & \text{if } 3 \leq x < \inf  \end{cases}$
This is a right continuous function, meaning any point is continuous if approached from the right hand side. Also, the size of the jump at any point is equal to $P(X = x)$
Theorem: The function F(x) is a CDF if and only if the following three conditions hold:
a) $\lim_{x\rightarrow \inf} F(x) = 0$, and $\lim_{x \rightarrow \inf} F(x) = 1$
b) $F(x)$ is a nondecreasing function of x
c) $F(x)$ is right-continuous, meaning for every number $x_0, \lim_{x \downarrow x_0} F(x) = F(x_0)$
ex) The number of tosses required to get a head if $p$ is the probability of getting a head on a given toss, has the probability function $P(X=x) = (1 * p)^{x-1}p$ where $x$ is the random variable that counts the number of tosses needed to get a head. $P(X \leq x) = \sum_{i=1}^x P(X = i) = \sum_{i=1}^x (1 * p)^{i-1}p$. Since $\sum_{l=1}^n t^{l-1} = \frac{1 * t^n}{1 * t}$(since $\sum_{i=0}^n ar^n = a + a\sum_{i=1}^n r^n = a\frac{1 -r^{n+1}}{1-r} \Rightarrow \sum_{i=1}^n r^n =  \frac{1 -r^{n+1}}{1-r} * 1 = \frac{r(1-r^n)}{1-r} \Rightarrow \sum_{i=1}^n r^{n-1} = \frac{1-r^n}{1-r})$, $F_X(x) = P(X \leq x) = \frac{1 * (1-p)^x}{1-(1-p)}p = 1 * (1-p)^x, x \in N \,$. This is called a geometric distribution.
ex) A continuous CDF example is the function $F_X(x) = \frac{1}{1+e^{-x}}$, which can be shown to satisfy all three conditions. For the first, $\lim_{x\rightarrow -\inf} F_X(x) = 0$ since $e^{-x}$ diverges in this limit, and $\lim_{x\rightarrow \inf} F_X(x) = 1$ since $e^{-x}$ vanishes in this limit. For the increasing property, $\frac{d}{dx}F_X(x) = \frac{e^{-x}}{(1+e^-x)^2}$ is always greater than 0, meaning that $F_X(x)$ is always increasing. $F_X(x)$ is fully continuous since $e^{-x}$ is fully continuous, meaning it is of course right continuous. This is an example of a logistic distribution.
A CDF can be formed from a set of continuous functions too, with discontinuity being the situation at a finite number of points.
A random variable X is defined to be continuous if $F_X(x)$ is a continuous function of x and discrete if $F_X(x)$ is a step function.
The random variables $X$ and $Y$ are identically distributed if for every set $A \in B^1 ,P(X \in A) = P( Y \in A)$ where $B^1$ is the smallest sigma algebra containing all intervals of real numbers of the form $(a,b),[a,b),[a,b],(a,b]$. Note if probabilities are defined for a larger class of the set, it is possible that two random variables have the same distribution function but not the same prob for every given event, meaning the CDF does not completely define the probability distribution it is associated with, (not 1-1).
Theorem: The following two statements are equivalent
a) Two random variables are identically distributed.
b) They have the same CDF.
Associated with a random variable X and its CDF is another function, called the probability density function, pdf, or probability mass function, PMF, in the continuous and discrete situations respectively
The probability mass function of a discrete variable X is given $f_X(x) = P(X=x)$ for all x.
ex) The geometric distribution from before has the PMF $f_X(x) = P(X = x) = \begin{cases} (1-p)^{x-1}p& \text{ for } x = 1,2,... \\ 0 & \text{ otherwise}\end{cases}$.
$P(a \leq X \leq b) = \sum_{k=a}^bf_x(k)$ with the special situation $P(X \leq b) = F_X(b)$
For the continuous situation, the probability density function is defined as $P(X \leq x) = F_X(x) = \int_{-\inf}^xf_X(t)dt$. Using the Fundamental Theorem of Calculus with the assumption that $f_X(x)$ is continuous, which is true $\frac{d}{dx} F_X(x) = f_X(x)$
Either the CDF or the PMF, pdf can be used to solve problems, and the simpler one should be chosen
ex) For the logistic distribution, $F_X(x) = \frac{1}{1+e^{-x}}$. $f_X(x) = \frac{e^{-x}}{(1+e^{-x})^2}$. The area under the curve gives the interval probabilities.
Theorem: A function $f_X(x)$ is a pdf or PMF of a random variable X if and only if
a) $f_X(x) \geq 0$ for all $x$
b) $\sum_x{f_X(x)} = 1$ or $\int_{-\inf}^\inf f_X(x)dx = 1$
Mathematically, any non-negative function with a finite positive integral or sum can be turned into a pdf or PMF. There are edge cases where $F_X(x)$ is continuous but not discrete, but those can be ignored for now, meaning to restrict the class of functions.
  