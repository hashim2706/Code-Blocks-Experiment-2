# Code-Blocks-Experiment-2

📡 Implementation of Go-Back-N Protocol – Selective Repeat

## 🎯 Aim

To write and execute a program for the Go-Back-N protocol using the Selective Repeat technique.

🛠️ Equipments Required

• 	Personal Computer

• 	Turbo C Compiler

## 📋 Procedure
1. 	Connect two computers in a Wired/Wireless LAN.
2. 	Ensure both computers are on the same network and can ping each other.
3. 	Open a new C file in Code::Blocks or any C IDE and type the program.
4. 	Navigate to:
Project -> Properties -> Project Build Options -> Linker Settings
Add: netproto and pthread
5. 	Execute the program on both server and client machines.
6. 	Enter the following:
• 	IP address of the remote machine
• 	Port address of both local and remote machines
• 	Error rate
7. 	Choose the file and verify the Go-Back-N protocol operation.

## 💻 Program
```txt

#include <stdio.h>
#define MAX_FRAMES 100

int main() {
    int i, j, n;
    char frame[MAX_FRAMES + 1][10]; // Fixed size array

    printf("GO BACK N ARQ\n");
    printf("Enter number of frames (max %d): ", MAX_FRAMES);
    scanf("%d", &n);

    if (n > MAX_FRAMES || n < 1) {
        printf("Invalid number of frames! Please enter between 1 and %d\n", MAX_FRAMES);
        return 1;
    }

    for (i = 1; i <= n; i++) {
        printf("Content for frame %d: ", i);
        scanf("%9s", frame[i]); // Limit input to prevent buffer overflow
    }

    printf("Enter frame number with no ACK: ");
    scanf("%d", &j);

    // First transmission attempt - send all frames
    printf("\n--- Initial Transmission ---\n");
    for (i = 1; i <= n; i++) {
        printf("Sending frame %d: %s\n", i, frame[i]);
        if (i != j) {
            printf("FRAME %d ACKNOWLEDGED...\n", i);
        } else {
            printf("Frame %d - NO ACKNOWLEDGMENT RECEIVED\n", i);
        }
        printf("\n");
    }

    // Go-Back-N: Retransmit from error frame onwards
    if (j >= 1 && j <= n) {
        printf("--- Go-Back-N Retransmission ---\n");
        printf("No Acknowledgment for frame %d...\n", j);
        printf("Retransmitting all frames from frame %d onwards:\n\n", j);

        for (i = j; i <= n; i++) {
            printf("Resending frame %d: %s\n", i, frame[i]);
            printf("FRAME %d ACKNOWLEDGED...\n", i);
            printf("\n");
        }
    } else {
        printf("Invalid frame number entered.\n");
    }

    printf("ALL FRAMES RECEIVED SUCCESSFULLY\n\n");

    return 0;
}
```


## 🖥️ Sample Output
<img width="1920" height="1080" alt="Screenshot (255)" src="https://github.com/user-attachments/assets/a35a58b0-1f12-48fc-ac84-2a181400b4ae" />


## ✅ Result

Thus, the Go-Back-N protocol using Selective Repeat was successfully implemented and verified.
