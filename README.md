# VELSYNC_VCD_02
This project implements a Finite State Machine (FSM)-based Traffic Light Controller for a highway and a country road intersection. It uses an internal delay counter to manage transition delays without inserting extra wait states.

# 🔄 Process of the Traffic Signal Controller Code

# 1.Clock and Reset

* The design works on the positive edge of the clock (clk).
* When reset (rst) is high, the FSM is initialized to a known state (RED).

# 2.State Register

* A register stores the current state of the traffic signal.
* On every rising clock edge:
* If rst = 1, state is set to RED.
* If rst = 0, state updates to the next state.

# 3.Next-State Logic

* This block decides which state comes next:
 * GREEN → YELLOW
 * YELLOW → RED
 * RED → GREEN
 * The decision depends only on the current state.

# 4.Output Logic

* Outputs depend only on the current state (Moore FSM).
* only one light is ON at a time:
* GREEN state → green = 1
* YELLOW state → yellow = 1
* RED state → red = 1

# 5.Continuous Operation
* After reset is released, the FSM cycles continuously through all three states on each clock edge.

# 6.Text State Diagram
          +--------+      +---------+      +------+
          | GREEN  | ---> | YELLOW  | ---> | RED  |
          +--------+      +---------+      +------+
                ^                               |
                +-------------------------------+

