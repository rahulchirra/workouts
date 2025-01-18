# Part II: Advanced Techniques

## Chapter 5: Evaluation Metrics

**Introduction:**
This chapter explores the crucial topic of evaluating generative AI models, which is challenging since generative models are trained to create data, rather than to classify or make predictions on data. This means that a model’s success must be determined by the quality of the data it produces, which is often subjective, and requires different types of evaluation techniques, many of which rely on heuristics or on pre-existing trained models. In this chapter, we will cover different evaluation metrics for images, text and other data types, also exploring how we can use human evaluations to measure the subjective quality of the generated data.

### 5.1 Introduction to Evaluation Metrics

*  **Concept:**
    *   Evaluation metrics in generative AI aim to provide a quantitative measure of the quality of generated data samples, assessing their similarity to real data, their diversity, and their overall usefulness.
     * It's important to note that in generative AI, the goal is not to predict or classify data, but rather to generate novel instances of it. There is often no "ground truth" as new samples may be completely new data points.
  *  Due to this aspect, evaluation can be hard and there is no single universal metric that can accurately assess the overall quality of the generated data.
*   **Challenges:**
       *  Developing metrics that accurately reflect the complex nature of human perception and creativity.
       *  Quantifying the diversity, novelty, and coherence of generated outputs.
      *  Creating automated metrics for evaluating subtle differences in quality.
*   **Human Evaluation:**
    *   In many situations, human evaluation is a critical step: Human raters assess and judge the quality and realism of generated content based on subjective factors.
     *  Such methods require well-designed user studies, where participants give a subjective rating or ranking of different aspects of the generative model output.
      *  The collected responses from the user studies are aggregated using different techniques to provide a final subjective rating.
### 5.2 Metrics for Image Quality

*   **Inception Score (IS):**
     *   **What it measures:** The Inception Score aims to quantify the quality and diversity of generated images by calculating the classification probabilities of generated samples using a pre-trained image classification model.
        * A well designed model, with diverse and realistic samples will tend to predict a single class with high probability (high score), but over different samples.
    *   **How to calculate it**:
         1. Pass the generated images through a pre-trained classification network (e.g., Inception).
         2. For each image, compute the probability distribution over the classes.
        3. Calculate the KL divergence between the class distribution and the uniform distribution across all classes, and average the results.
        *   A higher IS indicates higher quality and diversity of generated images.
    *  **Limitations:** It may not accurately capture the similarity of generated samples to real world images.
*   **Fréchet Inception Distance (FID):**
    *  **What it measures:** FID provides a measure of similarity between the distribution of generated images and the distribution of real images, using the feature space of a pre-trained image classification network.
        *   Compares the generated images to real world images by analysing their internal representations (feature vectors).
     *   **How to calculate it**:
           1. Pass both generated and real images through a pre-trained network (e.g. Inception network) and get their feature vectors from a specific layer.
          2.  For both real and generated data, compute the mean and covariance matrices based on the extracted features.
         3. Calculate the Frechet distance between these two multivariate Gaussian distributions.
         *  A lower FID indicates that generated images are more similar to the real data distribution.
      *  **Limitations:** Fails to measure diversity.
*  **Other metrics:**
        * **Kernel metrics**: Compare distributions of generated samples to the distribution of real samples based on statistical kernel distances.
          *   **Precision and Recall**: Evaluate the overlapping between real and generated data distributions.
         *   **Visual Quality**: Human studies that assess qualities such as image resolution and sharpness.

### 5.3 Metrics for Text Quality

*   **BLEU (Bilingual Evaluation Understudy):**
    *    **What it measures**:  Used primarily for evaluating machine translation performance, using a measure of similarity between predicted text and reference text.
        *   It measures the overlap of n-grams (sequences of n words) between the generated output and reference text.
     *   **How to calculate it**:
          *  Calculates the matching n-grams (sequences of words of length n) between the generated and reference text.
          *  Calculates a weighted average precision of n-gram matching.
          *   Higher BLEU scores indicate better translation quality.
    *   **Limitations**:
          *   Based on n-gram matching and may not capture semantic relationships or broader context.
          *   Does not capture grammatical correctness.
*   **ROUGE (Recall-Oriented Understudy for Gisting Evaluation):**
        *   **What it measures:** Evaluates text summarization tasks, measuring overlap between generated summaries and reference summaries.
        *   **How to calculate it:**
              *  Calculates the matching n-grams between the generated and reference summaries.
           *   Calculates recall based on how well the generated summary includes important information from the reference summary.
     *  **Limitations:**  Does not capture semantic meanings and may prioritize matches over semantic understanding.
*  **Perplexity:**
       *   **What it measures:**  Evaluates how well a language model can predict text sequences, assessing the model’s uncertainty in its predictions on a dataset.
       *    **How to calculate it:** Calculates the inverse probability of the training set, based on the probability distribution defined by a language model.
         *    Lower perplexity means that the model is more confident in predicting the text, and usually means that the text is more realistic, although not necessarily more high-quality.
   *  **Other metrics:**
        *   **Semantic Similarity:** Uses pre-trained models to assess the semantic similarity between the generated and real text.
      *  **Human evaluation techniques:** Human ratings are important to assess the quality and coherence of generated text.

### 5.4 Metrics for Other Data Types

*   **Audio:**
      *   **Signal Quality Metrics:** Common signal based metrics such as signal-to-noise ratios (SNR) and other measures to measure the quality of audio signals.
       *  **Intelligibility Metrics:** Metrics that assess the clarity and intelligibility of the generated audio such as Mean Opinion Score (MOS), or Short-Time Objective Intelligibility Measure (STOI).
     *   **Comparison of spectrograms:** Comparing time-frequency representation of audio.
     *    Comparing distributions of different audio features extracted from real and fake samples.

*   **Video:**
     *   **Motion and Content Similarity**: Combination of image quality metrics for individual frames and metrics that measure the temporal consistency of the video sequence.
      *   **Object Tracking Metrics**: Assessing the accuracy of the location of the objects during video.
       *  **Flow Related Metrics:** Assessing the movement of the objects and background in videos.
     *   **Human Evaluation:** User studies to assess the quality and realism of generated video.
*  **Sensor Data:**
      *   **Time series forecasting metrics:** Methods for assessing the model’s ability to fit to the time-series data (such as RMSE, MAE etc).
       *  **Statistical metrics**: Evaluation based on comparisons of distributions and correlations between different variables.
          *   Specialized Metrics: application-specific metrics that are designed for the targeted application

### 5.5 Challenges and Limitations of Current Evaluation Metrics

*   **Lack of Ground Truth:**
    *  Generative models produce novel samples which may not have a direct counterpart in the real world or dataset. This often requires developing metrics that don’t rely on comparisons to ground truth data.
      *   This lack of ground truth makes automatic evaluation very difficult and often leads to metrics that are not well correlated with human judgements.
*   **Subjectivity of Human Perception:**
     *  Human judgement is crucial for assessing certain aspects of data quality.
    *   Metrics that capture creativity, artistic style, emotional impact, and other such subjective aspects are still lacking.
         *  It is difficult to capture human perception using automated metrics.
         *  Human evaluation is more expensive and may not be practical for all applications.
*   **Capturing diversity:**
       *  Many metrics focus on fidelity and quality of generated samples, often failing to quantify the diversity of the generated samples.
       *   A model that can produce very high-quality but similar data samples will get a high fidelity score but low diversity.
    *   Developing metrics that capture both the fidelity and diversity is a very important ongoing research problem.
*   **Computational Complexity and Metric Selection:**
        *   Computing some evaluation metrics, such as FID or other kernel metrics, may require significant computational time, limiting their usage.
         *  Also, developing metrics that are appropriate for every modality and every task is extremely difficult.

*   **Examples:**
        *   Illustrate how the same model can perform very differently when evaluated using different metrics.
       *   Use an example to demonstrate the shortcomings of commonly used evaluation metrics in capturing all aspects of human perception.
         *  Highlight open research problems that are focused on developing better automated metrics for generative AI.

*   **Activities:**
      *   Implement and experiment with various metrics used in generative AI to evaluate different model outputs.
       *   Design human studies to collect subjective data on the generated outputs of generative models.
       *  Perform a literature survey on research focused on evaluation of generative models.
