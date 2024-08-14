# Anomaly Detection for Financial Fraud with Autoencoder Neural Networks
## **Objective**
The primary objective of this project is to develop a robust fraud detection system for financial transactions using Autoencoder Neural Networks, leveraging data akin to real-time SAP ERP system data. The autoencoder model will be trained to accurately reconstruct regular transaction data, resulting in a low reconstruction loss (below a certain threshold) for these typical patterns. However, when faced with anomalous transactions that deviate from the norm, the model is expected to exhibit a higher reconstruction loss (above a certain threshold), thereby signaling potential fraudulent activity. A key aspect of this project involves visualizing the reconstruction loss across various transactions to clearly distinguish between normal and anomalous behavior.

## **Softwares & Frameworks**
<img src="https://github.com/KolanHarsha/DDos-detection-Using-Machine-Learning/assets/110462466/ec05c02a-389a-4363-8b8c-9b1ba8ca28b0" alt="python" width="150" height="100">
<img src="https://github.com/user-attachments/assets/0d094a07-6ebd-4b8e-9cb2-f0d44e69b98d" alt="python" width="150" height="100">

## **Model Architecture**

![image](https://github.com/user-attachments/assets/ddf90c93-0b87-4177-a242-f4ce060731ff)

## **Model Training**

The encoder consists of a dense layer with a Leaky ReLU activation function, taking an input with a shape of 618 and producing an output with a shape of 3. Similarly, the decoder is another dense layer with a Leaky ReLU activation, which reconstructs the encoder's output froTm a shape of 3 back to the original shape of 618. After the autoencoder processes the input data, the difference between the original input and its reconstructed version (output) is calculated. This difference is referred to as the reconstruction loss, any data point with a reconstruction loss higher than the threshold could be considered anomalous.

The AENN is trained for 25 epochs, using binary cross-entropy as the loss function and the ADAM optimizer. The training statistics are presented below.

![image](https://github.com/user-attachments/assets/5052b760-9099-4e40-916c-63f91d13ed29)

The encoder and decoder weights for the 25th epoch are available at "encoder_model_epoch_25.pth", "decoder_model_epoch_25.pth" files.

## **Model Evaluation**
The 95th percitle of the reconstruction loss is set as threshold.
```bash 
threshold = np.percentile(reconstruction_loss_transaction, 95) 
```

The figure below shows the performance of AENN for anomaly detection.
![image](https://github.com/user-attachments/assets/da333142-fb73-49ac-b141-a05a34c3270a)


## **Inference**

We already have the labels in our dataset indicating regular, local and global anomalies. The figure below is the plot of reconstruction loss along with already available labels.

![image](https://github.com/user-attachments/assets/5ed804f2-1155-4ae7-9c41-dca57939ad3b)

This figure is almost similar to the one above hence we can infer that the decoder will be able to reconstruct the original data for regular transactions hence the loss is very low (below threshold) where as the loss is high (above threshold) for some cases which indicates these are anomalous one's.

## **Contributors**
- Sai Harsha Vardhan Reddy, Kolan- skolan@horizon.csueastbay.edu, harsha62334@gmail.com

Thanks for reading!
