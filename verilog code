`timescale 1ns / 1ps
//--------------------------------------------------
// Traffic Signal Controller using FSM
//--------------------------------------------------
module traffic_signal (
    input  clk,
    input  rst,
    output reg green,
    output reg yellow,
    output reg red
);

    // State encoding
    parameter GREEN  = 2'b00;
    parameter YELLOW = 2'b01;
    parameter RED    = 2'b10;

    reg [1:0] state, next_state;

    // State register (Sequential logic)
    always @(posedge clk) begin
        if (rst)
            state <= RED;     // Initial state
        else
            state <= next_state;
    end

    // Next-state logic (Combinational)
    always @(*) begin
        case (state)
            GREEN:  next_state = YELLOW;
            YELLOW: next_state = RED;
            RED:    next_state = GREEN;
            default:next_state = RED;
        endcase
    end

    // Output logic (Moore FSM)
    always @(*) begin
        // Default OFF
        green  = 0;
        yellow = 0;
        red    = 0;

        case (state)
            GREEN:  green  = 1;
            YELLOW: yellow = 1;
            RED:    red    = 1;
        endcase
    end

endmodule
