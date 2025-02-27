package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;

@TeleOp(name = "Mecanum Drive Linear", group = "TeleOp")
public class FirstTelop extends LinearOpMode {


   // private DcMotor frontLeft;
   // private DcMotor frontRight;
   // private DcMotor rearRight;

    @Override
    public void runOpMode() {
        DcMotor frontLeft = hardwareMap.get(DcMotor.class, "frontLeft");
        DcMotor rearLeft = hardwareMap.get(DcMotor.class, "rearLeft");
        DcMotor frontRight = hardwareMap.get(DcMotor.class, "frontRight");
        DcMotor rearRight = hardwareMap.get(DcMotor.class, "rearRight");

        frontLeft.setDirection(DcMotorSimple.Direction.FORWARD);
        rearLeft.setDirection(DcMotorSimple.Direction.FORWARD);
        frontRight.setDirection(DcMotorSimple.Direction.REVERSE);
        rearRight.setDirection(DcMotorSimple.Direction.REVERSE);

        waitForStart();

        while (opModeIsActive()) {
            double y = -gamepad1.left_stick_y;
            double x = gamepad1.left_stick_x;
            double rotation = gamepad1.right_stick_x;

            double frontLeftPower = y + x + rotation;
            double rearLeftPower = y - x + rotation;
            double frontRightPower = y - x - rotation;
            double rearRightPower = y + x - rotation;

            double maxPower = Math.max(Math.abs(frontLeftPower), Math.abs(rearLeftPower));
            maxPower = Math.max(maxPower, Math.abs(frontRightPower));
            maxPower = Math.max(maxPower, Math.abs(rearRightPower));

            if (maxPower > 1.0) {
                frontLeftPower /= maxPower;
                rearLeftPower /= maxPower;
                frontRightPower /= maxPower;
                rearRightPower /= maxPower;
            }

            frontLeft.setPower(frontLeftPower);
            rearLeft.setPower(rearLeftPower);
            frontRight.setPower(frontRightPower);
            rearRight.setPower(rearRightPower);

            telemetry.addData("Front Left Power", frontLeftPower);
            telemetry.addData("Rear Left Power", rearLeftPower);
            telemetry.addData("Front Right Power", frontRightPower);
            telemetry.addData("Rear Right Power", rearRightPower);
            telemetry.update();
        }
    }
}
