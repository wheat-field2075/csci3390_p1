# CSCI3390 Project 1
Authors: Michael Lin and Matt Smallhouse

## Part (a)
k = 2
* xS = 7216451796612181716146191
* hash_value = 0056ffe4a6e27174738937bd38bcd712e995ea6d6763a2280c61d34fb0d2c1e6
* time_elapsed = 1s
* number_of_trials = 1000

k = 3
* xS = 7884167556612181716146191
* hash_value = 0001212c0a2d1ec6075d8cdd362cf82f8928f790587aa07b495b8bdde7f9a890
* time_elapsed = 1s
* number_of_trials = 16000

k = 4
* xS = 13658588486612181716146191
* hash_value = 00005100e60ba43c3b4a107ad47e08aef208315b5476b5bf94d2fe256ac67042
* time_elapsed = 1s
* number_of_trials = 256000

k = 5
* xS = 12207163986612181716146191
* hash_value = 00000dfc22b93ac5c893281c151fc0e82de11fde78d6ef4f85f2ed11b0c32f5a
* time_elapsed = 2s
* number_of_trials = 4096000

k = 6
* xS = 893410396612181716146191
* hash_value = 00000085d0f5c11ab53ab342bf4fe81dda966e70bceef1cbc7aac9fe78032557
* time_elapsed = 17s
* number_of_trials = 66536000

## Part (b)
k = 7
* xS = 1161529636612181716146191
* hash_value = 0000000385505794a20a328016333266777fe1d6b6ad869b9659bec6e0ad5355
* time_elapsed = 2587s
* number_of_trials = 1048576000
* description = The cluster is comprised of one master node (n2-standard-4) and two worker nodes (c2-standard-4). The master node is provided with 4 vCPUs (Intel Xeon Gold 6268CL) while each worker nodes has two 4 vCPUs (Intel Xeon Gold 6253CL).
* methodology = Since the hash is a hexadecimal number, I thought that for every sixteen solutions of difficulty [n], there would be one solution of difficulty [n + 1]. I found that running 1000 trials for difficulty 2 was capable of consistently giving solutions; for each single increase in difficulty, I increased the number of trials sixteenfold, which gave me answers consistently.

## Part (c)
To constrain the value of the nonce, we can change the line:

  `iter.map(x => rand.nextInt(Int.MaxValue - 1) + 1)`

to:

  `iter.map(x => rand.nextInt(difficulty - 1) + 1)`

This will not be more efficient than the randomized algorithm since the odds of having a generated nonce will work is [n / (16)^n], which approaches 0 as n increases. Therefore, even though the program will execute significantly faster, it's almost guranteed to be wrong.
