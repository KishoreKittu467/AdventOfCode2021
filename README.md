# AdventOfCode2021
My code for AdventOfCode2021 challenge

/**

--- Day 1: Sonar Sweep ---


       var increasedCount = 0

       fun getMeasurements(isCompleted: Boolean) {

            firebaseManager.getAllMeasurements {
                this.isCompleted = isCompleted
                
                val setSize = 3 // give second input here
                
                it.forEach { keyLocation ->
                    keyLocation.keyLocation?.split(" ")?.map { key -> key.toInt() }?.apply {
                        countDepthIncrements( this, setSize) 
                        orderList.value = map { key -> StoreAppointmentModel(range = key) }
                    }
                }
            }
        }
    
        fun countDepthIncrements(input: List<Int>, setSize: Int = 1) {
            input.apply {
            forEachIndexed { index, _ ->
                if (setSize != 0) {
                    var lastSetTotal = 0
                    val currentSetTotal = when {
                        index - 1 >= setSize -> {
                            lastSetTotal = subList(index - 1 - setSize, index - 1).sum()
                            subList(index - setSize, index).sum()
                        }
                        index >= setSize -> {
                            subList(index - setSize, index).sum()
                        }
                        else -> {
                            0
                        }
                    }
                    if (currentSetTotal > lastSetTotal) {
                        increasedCount++
                    }
                }
            }
            }
        }

// Outputs:

// Part One: Your puzzle answer was 1567.
// Part Two: Your puzzle answer was 1529.
