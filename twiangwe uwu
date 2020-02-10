#include "vex.h"
using namespace vex;

//#region config_globals
vex::brain      Brain;
vex::motor      right_drive(vex::PORT1, vex::gearSetting::ratio18_1, true);
vex::motor      left_drive(vex::PORT12, vex::gearSetting::ratio18_1, false);
vex::motor      tilt(vex::PORT3, vex::gearSetting::ratio36_1, true);
vex::motor      right_intake(vex::PORT4, vex::gearSetting::ratio18_1, true);
vex::motor      left_intake(v2ex::PORT5, vex::gearSetting::ratio18_1, false);
vex::motor      right_flywheel(vex::PORT6, vex::gearSetting::ratio18_1, true);
vex::motor      left_flywheel(vex::PORT11, vex::gearSetting::ratio18_1, false);


vex::competition Competition;

void pre_auton() {
  

}

void autonomous() {
   

}

void drivercontrol() {
    
    int tiltSpeedPCT = 20.00;
    int intakeSpeedPCT = 80.00;
    int flywheelSpeedPCT = 50.00;
    
    while (true) {
        
        
        //drive
        left_drive.spin(directionType::fwd, (con.Axis3.value() + con.Axis4.value())/2, velocityUnits::pct);
        //left joystick left drive
        right_drive.spin(directionType::fwd, (con.Axis2.value())/2, velocityUnits::pct);
        //right joystick right drive
        
        //rail tilt
        if(con.ButtonX.pressing()){ //x foward
            tilt.spin(directionType::fwd, tiltSpeedPCT, velocityUnits::pct);
        }
        else if (con.ButtonB.pressing()){ //b back
            tilt.spin.(directionType::rev, tiltSpeedPCT, velocityUnits::pct);
        }
        else { //none
            tilt.stop(brakeType::coast);
        }
        
        //intake rollers
        if(con.ButtonR1.pressing()){ //right upper shoulder in
            left_intake.spin(directionType::fwd, intakeSpeedPCT, velocityUnits::pct);
            right_intake.spin(directionType::fwd, intakeSpeedPCT, velocityUnits::pct);
        }
        else if (con.ButtonR2.pressing()){ //right lower shoulder out
            left_intake.spin(directionType::rev, intakeSpeedPCT, velocityUnits::pct);
            right_intake.spin(directionType::rev, intakeSpeedPCT, velocityUnits::pct);
        }
        else {
            left_intake.stop(brakeType::brake);
            right_intake.stop(brakeType::brake);
        }
        
        //flywheel
        if(con.ButtonL1.pressing()){ //left upper shoulder full speed
            left_flywheel.spin(directionType::fwd, flywheelSpeedPCT, velocityUnits:pct);
            right_flywheel.spin(directionType::fwd, flywheelSpeedPCT, velocityUnits::pct);
        }
        else {
            left_flywheel.stop(brakeType::brake);
            right_flywheel.stop(brakeType::brake);
        }
        }

    }
}

int main() {
    // Do not adjust the lines below

    // Set up (but don't start) callbacks for autonomous and driver control periods.
    Competition.autonomous(autonomous);
    Competition.drivercontrol(drivercontrol);

    // Run the pre-autonomous function.
    pre_auton();

    // Robot Mesh Studio runtime continues to run until all threads and
    // competition callbacks are finished.
}
