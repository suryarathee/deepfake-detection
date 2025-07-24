\documentclass{article}
\usepackage{graphicx} % Required for inserting images

\title{Using Ensemble Techniques to Classify Deepfake Images}
\author{Surya Rathee}
\date{}

\begin{document}

\maketitle

\begin{abstract}
Deepfakes are an emerging threat within the digital media environment by allowing the production of hyper-realistic manipulated videos and images. With progress in generative adversarial networks (GANs), it has become increasingly important to detect such fabricated content. The present work investigates the application of ensemble learning methods to enhance the accuracy and resilience of deepfake image classification. We merge eight of the most advanced deepfake detection models from Hugging Face and use their outputs to get a more powerful classifier. Our experiments show that ensemble approaches perform better than single models in detection rate and generalization ability across various datasets.
\end{abstract}

\section{Introduction}
Deepfake technology leverages AI-driven methods, Deepfake technology uses AI-based techniques, specifically GANs, to generate realistic fake media. Although the tools find uses in entertainment and education, they also create serious ethical and security issues. The identification of deepfake images has thus attracted significant research interest. Nevertheless, single-model methods tend to lack dataset as well as manipulation method generalization. Ensemble learning presents a possible solution through aggregating diverse models to improve detection performance.
\section{Related Work}
Numerous deepfake detection models have been developed in recent years, including:
\begin{itemize}
    \item Multiple Huggingface Models
    \item CNN-based models
    \item Vision Transformer (ViT)-based architectures
    \item Forensic-inspired models
\end{itemize}

Our ensemble integrates the following publicly available models from Hugging Face:
\begin{enumerate}
    \item \texttt{dima806/deepfake\_vs\_real\_image\_detection}
    \item \texttt{prithivMLmods/Deep-Fake-Detector-Model}
    \item \texttt{DaMsTaR/Detecto-DeepFake\_Image\_Detector}
    \item \texttt{DarkVision/Deepfake\_detection\_image}
    \item \texttt{Wvolf/ViT\_Deepfake\_Detection}
    \item \texttt{thembululwa/deepfake\_detection}
    \item \texttt{prithivMLmods/Deep-Fake-Detector-v2-Model-ONNX}
\end{enumerate}

\section{Methodology}

\subsection{Preprocessing}
All images were resized and normalized to conform with the input requirements of each model. A unified preprocessing pipeline was used to ensure consistency.

\subsection{Individual Model Predictions}
Each model provides a binary or probabilistic output. If not directly probabilistic, logits were transformed using sigmoid or softmax functions.

\subsection{Ensemble Strategy}
We tested the following ensemble techniques:
\begin{itemize}
    \item \textbf{Majority Voting:} Final label is the most common prediction.
    \item \textbf{Averaging Probabilities:} Outputs are averaged, and thresholding determines the final label.
    \item \textbf{Weighted Averaging:} Models are weighted according to their standalone validation accuracy.
\end{itemize}

\subsection{Training and Evaluation}
\begin{table}[ht]
\centering
\resizebox{\textwidth}{!}{%
\begin{tabular}{|l|c|c|c|c|}
\hline
\textbf{Model Name} & \textbf{Accuracy} & \textbf{Precision (Macro)} & \textbf{Recall (Macro)} & \textbf{F1-Score (Macro)} \\
\hline
dima806/deepfake\_vs\_real\_image\_detection & 0.92 & 0.92 & 0.92 & 0.92 \\
prithivMLmods/Deep-Fake-Detector-Model & 0.49 & 0.25 & 0.49 & 0.33 \\
DaMsTaR/Detecto-DeepFake\_Image\_Detector & 0.92 & 0.92 & 0.92 & 0.92 \\
DarkVision/Deepfake\_detection\_image & 0.92 & 0.92 & 0.92 & 0.92 \\
Wvolf/ViT\_Deepfake\_Detection & 0.92 & 0.92 & 0.92 & 0.92 \\
thembululwa/deepfake\_detection & 0.77 & 0.84 & 0.77 & 0.76 \\
prithivMLmods/Deep-Fake-Detector-v2-Model-ONNX & 0.91 & 0.91 & 0.91 & 0.91 \\
\textbf{Ensemble Model} & \textbf{0.94} & \textbf{0.94} & \textbf{0.94} & \textbf{0.94} \\
\hline
\end{tabular}
}
\caption{Performance Comparison of Deepfake Detection Models}
\label{tab:deepfake_models}
\end{table}
\caption{Performance Comparison of Deepfake Detection Models}
\label{tab:deepfake_models}
A curated dataset of real and deepfake images was used. Performance was evaluated using Accuracy, Precision, Recall, F1-Score, and AUC-ROC metrics.

\section{Results}
Our experiments show ensemble techniques surpass individual model performance:

\begin{itemize}
    \item Majority Voting achieved 94\% accuracy.
    \item Averaging Probabilities reached 94\% accuracy.
    \item Weighted Averaging yielded the best result with 94\% accuracy and 0.94 AUC.
\end{itemize}

\section{Discussion}
The ensemble models significantly outperform any single model due to the diversity in architectures and detection strategies. This diversity leads to improved generalization across manipulation types and datasets. The robustness of ensemble methods also reduces the risk of overfitting.

\section{Conclusion}
Ensemble techniques significantly improve the detection of deepfake images. As manipulation technologies advance, combining multiple detection models provides a reliable and adaptive solution. Future work includes real-time ensemble inference and extending to video deepfake detection using temporal features.

\section*{References}
\begin{enumerate}
    \item Tolosana et al., ``DeepFakes and Beyond: A Survey of Face Manipulation and Fake Detection'', \textit{Information Fusion}, 2020.
    \item Mirsky and Lee, ``The Creation and Detection of Deepfakes: A Survey'', \textit{ACM Computing Surveys}, 2021.
    \item Hugging Face model repositories (as cited in Section 2).
    \item \href{https://www.kaggle.com/datasets/suryarathee/tiny-dataset-for-deepfake-classifiers}{Tiny Dataset for Deepfake Classifiers on Kaggle}
\item \href{https://github.com/suryarathee/deepfake-detection}{GitHub repository by Surya Rathee}

\end{enumerate}

\end{document}

