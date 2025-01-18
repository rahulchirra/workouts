## Chapter 5: Evaluation Metrics

**Introduction:**
This chapter will explore the crucial topic of evaluating generative AI models, which is challenging since generative models are trained to create data, rather than to classify or make predictions on data. This means that a model’s success must be determined by the quality of the data it produces, which is often subjective, and requires different types of evaluation techniques, many of which rely on heuristics or on pre-existing trained models. In this chapter, we will cover different evaluation metrics for images, text and other data types, also exploring how we can use human evaluations to measure the subjective quality of the generated data.

### 5.1 Introduction to Evaluation Metrics

*  **Concept:**
    *  Evaluation metrics in generative AI aim to quantify the quality of generated data samples by assessing their similarity to real data, their diversity, and their overall quality.
   *  The challenge in generative AI evaluation is that there is no single metric that can accurately capture all aspects of human perception and creativity, and there is no ground truth to compare with since generated samples are often novel instances.
    *  Metrics try to capture aspects such as fidelity, diversity, novelty, and coherence of the generated data samples
*   **Challenges:**
        *   Developing metrics that accurately capture the complex and subjective nature of human perception and creative output.
        *  Defining metrics that can capture the overall diversity, novelty, and coherence of generated outputs.
        * Developing automated metrics for high quality samples.
    * **Human Evaluation:**
      * In many situations it is necessary to involve human raters to evaluate the overall quality and realism of generated content.
        * This is useful when the quality metrics fail to capture subtleties of human experience and creative perception.
         * Human evaluation includes user studies, where participants rate different aspects of the generated content, and their subjective opinions are then aggregated to provide the final rating.

### 5.2 Metrics for Image Quality

*   **Inception Score (IS):**
        *   Measures the diversity and quality of generated images.
        *   Based on the classification performance of a pre-trained image classification network, such as Inception.
       * Calculates the classification probabilities over all classes given generated samples, such that sharp predictions for a single class indicates high quality samples, while diverse predictions indicate high variety in generated samples.
        *   The higher the IS, the more the images are diverse and high quality.
     * **Limitations:** IS does not compare the generated distribution to the real data distribution and hence may not give reliable results.
*   **Fréchet Inception Distance (FID):**
        *   Compares the distribution of generated images to the distribution of real images using a distance measure.
        *  Based on the activations of a pre-trained image classification network, such as Inception.
        *   It captures the distance in the high dimensional feature space, rather than using a pixel by pixel comparison.
         *   The lower the FID, the more similar the generated images are to real images.
    *  **Limitations**: Does not measure diversity in the generated samples.
        *   Often combined with IS to capture both diversity and fidelity of generated images.
  *   **Other metrics:**
        *  **Kernel metrics**: Compare the distributions based on kernel density estimation.
         *   **Precision and Recall** metrics: used to evaluate the overlapping between generated and original data distributions, which provide better evaluation of the performance of generative models.
         *   **Visual Quality**: Assessing the visual quality of the generated images by using measures such as image resolution and sharpness, which often requires human judgement.

### 5.3 Metrics for Text Quality

*   **BLEU (Bilingual Evaluation Understudy):**
    *  Used primarily for evaluating machine translation.
       * Measures similarity between predicted text and reference text using n-gram matching, that is counts of the number of matching words or phrases between the two.
        *   Higher BLEU scores mean that the generated output is more similar to the reference text (high quality translation)
    *   **Limitations:** BLEU has several limitations since it is based on n-gram matching, and may fail to capture semantic aspects or broader context.
*   **ROUGE (Recall-Oriented Understudy for Gisting Evaluation):**
    *   Used primarily for evaluating text summarization
        * Measures the overlap between a generated summary and a reference summary, using the recall or precision based on n-gram matches.
        *  Focuses on matching the important content of the reference text in the generated summary.

    *  **Limitations:** Does not capture semantic meanings.
   * **Perplexity**:
        *   Used for evaluating the performance of language models by computing the probability of a generated text sequence given a trained language model.
       * A lower perplexity score indicates that the language model is more confident in predicting the text sequence.
    *  **Limitations**: Does not directly measure quality of the generated output, but a low perplexity does indicate that the text is more realistic.
  *  **Other metrics:**
         *  Semantic similarity: Use pretrained models to check semantic similarity between generated and real text.
          * Human evaluation techniques are still important for evaluating text generation.

### 5.4 Metrics for Other Data Types

*   **Audio:**
    *   Metrics to assess audio quality, such as Mean Opinion Score (MOS), or Short-Time Objective Intelligibility Measure (STOI).
    *    Using spectrograms and comparing distributions between real and fake audio.
    *  Measures of audio realism.
*   **Video:**
    *   Using a combination of image quality measures and metrics that measure the temporal consistency of the video.
     *   Object tracking metrics and flow related metrics to assess movement in videos.
     *  Content similarity based on extracted features and embeddings.
*   **Sensor data:**
     *   Time series forecasting metrics.
      * Analysis of distributions, and correlation between multiple dimensions, and more specialized metrics based on the task.

*  **Activities:**
    *   Implement different image quality metrics for image datasets.
    *   Evaluate the performance of a language model using perplexity and BLEU metrics on a text generation task.
      *   Design a user study to evaluate the realism of generated audio and video content.

### 5.5 Challenges and Limitations of Current Evaluation Metrics

*   **Lack of Ground Truth:** Generative models produce novel data samples, which don't have direct counterparts in a dataset. This makes it hard to evaluate with metrics that rely on comparing predicted values to real values.
*  **Subjectivity of Human Perception:** Aspects like creativity, artistic style, or emotional content are subjective and difficult to quantify accurately.
    *   Humans are better at detecting very subtle errors and inconsistencies in the generated output.
   *     Human studies are expensive, and it is not always possible to perform these for every experiment or every model.
*    **Capturing diversity:** Many metrics often focus on fidelity or quality but often fail to measure the diversity of the generated output.
        * A model that produces high quality but very similar samples will have high fidelity score but low diversity.
       * Finding metrics that can quantify both fidelity and diversity at the same time are still an active area of research.
    *   **Computational complexity:** Calculating some evaluation metrics such as FID may take significant time and resources, limiting their applicability for all tasks.
       *    There is also the problem of selecting the right type of metrics for various tasks and data.

*   **Examples:**
        * Show how a model performs using different evaluation metrics.
         *   Discuss the advantages and disadvantages of different types of metrics in the context of various generative tasks.
        *  Analyze the problems in current state of the art evaluation metrics and the open research questions to address these issues.
*   **Activities:**
    *   Analyze the limitations of commonly used evaluation metrics and discuss open research questions.
     * Design and implement evaluation methods for assessing the performance of generative models, for a specific problem, and justify your choice.
     * Perform a literature survey and review the most recent papers focusing on evaluation of generative models.
