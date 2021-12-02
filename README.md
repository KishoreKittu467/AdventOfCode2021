# AdventOfCode2021

My code for AdventOfCode2021 challenge

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

--- Day 2: Dive! ---

       fun getDirections(isCompleted: Boolean) {
   
            firebaseManager.getAllDirections {
                this.isCompleted = isCompleted

                it.forEach { direction ->
                    direction.directions?.split(" ")?.apply {
                        calculateArea(this)
                        orderList.value = map {
                            StoreAppointmentModel(customerName = it)
                        }
                    }
                }
            }
       }

// Part One:
        private fun calculateArea(input: List<String>) {
        var totalX = 0
        var totalY = 0
        val distances = input.slice(1..input.size step 2).map { it.toInt() }
        input.slice(0 until input.size - 1 step 2).apply {
            forEachIndexed { index, direction ->
                when(direction) {
                    "forward" -> {
                        totalX += distances[index]
                    }
                    "backward" -> {
                        totalX -= distances[index]
                    }
                    "down" -> {
                        totalY += distances[index]
                    }
                    "up" -> {
                        totalY -= distances[index]
                    }
                }
            }
        }
        areaCovered = totalX * totalY
        }
       
// Part Two:
       private fun calculateArea(input: List<String>) {
        var totalX = 0
        var totalY = 0
        var aim = 0
        val distances = input.slice(1..input.size step 2).map { it.toInt() }
        input.slice(0 until input.size - 1 step 2).apply {
            forEachIndexed { index, direction ->
                when(direction) {
                    "forward" -> {
                        totalX += distances[index]
                        totalY += (aim * distances[index])
                    }
                    "backward" -> {
                        totalX -= distances[index]
                    }
                    "down" -> {
                        aim += distances[index]
                    }
                    "up" -> {
                        aim -= distances[index]
                    }
                }
            }
        }
        areaCovered = totalX * totalY
        }

 // Outputs:

// Part One: Your puzzle answer was 2215080.
       
// Part Two: Your puzzle answer was 864715580.
       
       
 
