# System-Identification-of-Festo-Didactic-doser-for-RL-training
Development of a Neural Network-based digital twin (NLARX) for a smart water tank system. Features Siemens PLC integration, MATLAB system identification, and PyTorch NLARX modeling to serve as a simulation environment for training Reinforcement Learning controllers, DDPG and TD3 controllers are trained on the model. Finally Sim-2-real,model is running on VGU-MST festo didactic doser system

1. EXTRACT ALL RAR FILES
   
2. --------------------------------------------------DATA COLLECTION------------------------------------------------------------

Step 1. Open the UnifiedRSrv.js file. 
Step 2. Update the "PLC_IP" variable to exactly match the network address of your target PLC device.
Step 3. Assign the "Slot_ID" variable to 2 for an S7-300 PLC.
Step 4. Modify the "host_IP", "user", "password", and "DBname" variables to match your local MySQL database configuration.
Step 5. Ensure your MySQL service is actively running and the target database exists before starting the script.
Step 6. Open your system command prompt or terminal directly inside the folder containing the UnifiedRSrv.js script file.
Step 7. Type node UnifiedRSrv.js into the terminal and press the enter key to execute the data logger.

<img width="1353" height="715" alt="code SQL table generation" src="https://github.com/user-attachments/assets/839585bf-afc2-4e77-b475-b5ad30ea1b4e" />

3.------------------------------------PLC COMMUNICATION----------------------------------------------------------------------
Step 1.Please set the PC in the same subnet as the PLC(192.168.1.xxx)
Step 2. Then upload TIA portal program to PLC,accordingly
Step 3. Upload code to PLC
 4.-----------------------------------System identification-Reinforcement Learning---------------------------------------------
 
Step 1.	Run System identification model to get digital twin,we get NLARX model
 <img width="975" height="523" alt="image" src="https://github.com/user-attachments/assets/34b1317a-f7b0-49fa-8254-58e59593f5dd" />

Step 2.	Run iden2.mat if step 1 is not run
 <img width="975" height="523" alt="image" src="https://github.com/user-attachments/assets/2b0242b5-6e4b-4a97-81b0-9fb2913619ec" />

Step 3.	connect RL-Water-Tank in rlwatertank Simulink file and run DDPG.m or TD3.m or SAC.m to train agents.
 
 <img width="975" height="293" alt="image" src="https://github.com/user-attachments/assets/62c64877-8925-48e7-a47f-1465337ef7a1" />

 <img width="1003" height="477" alt="image" src="https://github.com/user-attachments/assets/17a282cc-771e-4cfc-8d4b-879322c62198" />
 <img width="991" height="513" alt="image" src="https://github.com/user-attachments/assets/0f96d719-3d67-4dc9-bdd5-e997b6f3f7c3" />


Step 4.	After training, change the subspace from “Water-Tank System” to “Water-Tank System Test Bench” and add a “Real-Time Sync” block for physical devices communication. Then press run, this model now run in real time
 <img width="975" height="405" alt="image" src="https://github.com/user-attachments/assets/95726cf8-15db-4569-9a42-3f7856604b45" />


You should follow the addresses defined in this project. Otherwise, you must configure manually modbus tcp/ip in matlab yourself.

5-------------------------------------------------System Identification with Python-----------------------------------------------
Step 1.Run arx_baseline.py to get arx model or nlarx_running_simulation.py to get nlarx model
 <img width="975" height="486" alt="image" src="https://github.com/user-attachments/assets/e01a4633-df58-42a8-be10-ca2a1c292f7f" />

Step 2.Run export_matlab.py to export to .mat file
 <img width="975" height="489" alt="image" src="https://github.com/user-attachments/assets/c02a518d-cae4-44c3-82de-dd320019346a" />

Step 3.Paste the nlarx_result.mat to matlab project, load the file in. Load Water-System Test Bench 1, go to Agent training and repeat the process

<img width="975" height="472" alt="image" src="https://github.com/user-attachments/assets/75c0b703-dd67-4b8c-9d8c-ee290b9b9365" />
