27. No
28. Sets all the elements of the array to 0
29. public void reset()
    {
        Arrays.fill(state, 0);
        // Seed the automaton with a single 'on' cell.
        state[numberOfCells / 2] = 1;
        state[numberOfCells / 2 - 1] = 1;
        state[numberOfCells / 2 + 1] = 1;
    }
30. public void update()
    {
        // Build the new state in a separate array.
        int[] nextState = new int[state.length];
        // Naively update the state of each cell
        // based on the state of its two neighbors.
        for(int i = 0; i < state.length; i++) {
            int left = (i == 0) ? 0 : state[i - 1];
            int center = state[i];
            int right = (i == state.length - 1) ? 0 : state[i + 1];
            
            nextState[i] = (left + center + right) % 2;
        }
        state = nextState;
    }
31. Nothing happens
32. public void update() {
    int left = 0;
    int center = state[0];
    for (int i = 0; i < state.length - 1; i
}
You only need to keep track of one old value at a time.
33. public void updateIterator(){
        int[] nextState = new int[state.length];
        int left = 0;
        int center = state[0];
        for (int i = 0; i < state.length; i++) {
             int right = (i < state.length - 1) ? state[i + 1] : 0;
             nextState[i] = (left + center + right) % 2;
             left = center;
             center = right;
        }
        state = nextState;
    }   
34. public int calculateNextState(int left, int center, int right){
        return (left + center + right) % 2;
    }
35. 