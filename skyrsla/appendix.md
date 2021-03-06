# Viðauki
## Dagbækur
Hér skal vera dagbók frá öllum í verkefninu
## robot-config.h file
```
vex::brain Brain;
vex::motor LeftMotor = vex::motor(vex::PORT1, false);
vex::motor RightMotor = vex::motor(vex::PORT10, true);
vex::motor ClawMotor = vex::motor(vex::PORT16);
vex::motor ArmMotor = vex::motor(vex::PORT19);
vex::gyro Gyro = vex::gyro(Brain.ThreeWirePort.A);
```

## main.cpp file fyrir HENDA Í RUSL
```
void turnLeft(int degrees){
    Gyro.startCalibration();
    vex::task::sleep(2000);
        
    LeftMotor.setVelocity(10, vex::velocityUnits::pct); 
    RightMotor.setVelocity(10, vex::velocityUnits::pct);
    while(abs(Gyro.value(vex::rotationUnits::deg)) < degrees){
        Brain.Screen.setCursor(1,0);
        Brain.Screen.print("Rotation: %f degrees", Gyro.value(vex::rotationUnits::deg));
        vex::task::sleep(100);

        LeftMotor.spin(vex::directionType::fwd); //Spin the left motor in the forward direction.
        RightMotor.spin(vex::directionType::rev); //Spin the right motor in the reverse direction.
    }
    LeftMotor.stop();
    RightMotor.stop();
}

void turnRight(int degrees){
    Gyro.startCalibration();
    vex::task::sleep(2000);
    
    LeftMotor.setVelocity(10, vex::velocityUnits::pct); 
    RightMotor.setVelocity(10, vex::velocityUnits::pct);
    while(abs(Gyro.value(vex::rotationUnits::deg)) < degrees){
        Brain.Screen.setCursor(1,0);
        Brain.Screen.print("Rotation: %f degrees", Gyro.value(vex::rotationUnits::deg));
        vex::task::sleep(100);

        LeftMotor.spin(vex::directionType::rev); //Spin the left motor in the forward direction.
        RightMotor.spin(vex::directionType::fwd); //Spin the right motor in the reverse direction.
    }
    
    LeftMotor.stop();
    RightMotor.stop();
}

void openClaw(){
    ClawMotor.spin(vex::directionType::rev, 50, vex::velocityUnits::pct);
    vex::task::sleep(500); //Sleep the task for a short amount of time to prevent wasted resources.
    ClawMotor.stop();
}

void closeClaw(){
    ClawMotor.spin(vex::directionType::fwd, 50, vex::velocityUnits::pct);
    vex::task::sleep(500); //Sleep the task for a short amount of time to prevent wasted resources.
    ClawMotor.stop();
}

void liftArm(){
    ArmMotor.spin(vex::directionType::fwd, 50, vex::velocityUnits::pct);
    vex::task::sleep(500); //Sleep the task for a short amount of time to prevent wasted resources.
    ArmMotor.stop(vex::brakeType::hold);
}

void dropArm(){
    ArmMotor.stop(vex::brakeType::brake);
}

void driveForward(int centimeters){
    vex::task::sleep(2000);
    
    double wheelDiameterCM  = 10.16;
    double travelTargetCM = centimeters; // CM
    
    double circumference = wheelDiameterCM * M_PI;
    double degreesToRotate = (360 * travelTargetCM) / circumference; 

    LeftMotor.setVelocity(20, vex::velocityUnits::pct); 
    RightMotor.setVelocity(20, vex::velocityUnits::pct);
    
    LeftMotor.rotateFor(degreesToRotate, vex::rotationUnits::deg, false); 
    RightMotor.rotateFor(degreesToRotate, vex::rotationUnits::deg); 
}


int main() {
    vex::task::sleep(2000);
    
    openClaw();
    closeClaw();
    turnLeft(180);
    liftArm();
    driveForward(100);
    turnRight(90);
    driveForward(55);
    openClaw();
    dropArm();
    turnLeft(180);
    driveForward(55);
    turnLeft(90);
    driveForward(100);
 
}
```

## main.cpp file fyrir PARTY MODE
```
int moveInCircle(){
	LeftMotor.setVelocity(80, vex::velocityUnits::pct);
    	RightMotor.setVelocity(80,vex::velocityUnits::pct);

    	LeftMotor.spin(vex::directionType::fwd);
    	RightMotor.spin(vex::directionType::rev);
    	vex::task::sleep(3000); 
    
    	LeftMotor.stop();
    	RightMotor.stop();
  	vex::task::sleep(1000);
    
    	LeftMotor.spin(vex::directionType::rev); 
    	RightMotor.spin(vex::directionType::fwd); 
    	vex::task::sleep(3000);
    
    	//Stop the motors
    	LeftMotor.stop();
    	RightMotor.stop();
    vex::task::sleep(1000);
    return 0;
}

int moveArm(){
	int armSpeedPCT = 50;
    	
    while(1){
        ArmMotor.spin(vex::directionType::fwd, armSpeedPCT, vex::velocityUnits::pct);
        vex::task::sleep(1000);
        ArmMotor.spin(vex::directionType::rev, armSpeedPCT, vex::velocityUnits::pct);
        vex::task::sleep(1000);
    }    
        
    return 0;
}

int main() {
    
    vex::task t1(moveInCircle);
    vex::task t2(moveArm);

  // Both function are now running an different thread
  // We need to wait for them to finish

    
}

```
