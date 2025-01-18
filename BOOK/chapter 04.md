# Part II: Advanced Techniques

## Chapter 4: Controlling Generative Models

**Introduction:**
This chapter explores various techniques that allow us to exert more control over the outputs of generative models. We've seen how generative models can create fantastic content, but controlling what they generate is very important for practical applications. Here, we will explore techniques such as conditional generation, style transfer, attribute manipulation, and latent space manipulation. We will also discuss how these methods can be applied and their limitations.

### 4.1 Conditional Generation

*   **Concept:**
    *  Conditional generation involves guiding the generative process of a model by providing additional input signals (conditions) that constrain the output to have certain characteristics. This allows for generating data that satisfies specific criteria.
     *  Instead of simply generating random data, conditional models learn to generate data based on the desired input conditions.
    *   The condition can be any form of data, such as:
          *   Class labels (e.g., generating only images of cats).
          *  Text descriptions (e.g., generating an image based on a textual prompt).
           * Other data modalities such as audio for generating video with specific audio characteristics.
*   **Techniques:**
    *  **Providing labels as inputs to the generator and the discriminator**: Used in Conditional GANs to condition generated output based on label or class information.
         * This is achieved by concatenating the input noise with a label embedding and providing this combined input to the generator. Similarly, the discriminator receives both data samples and the corresponding label.
     *    **Incorporating text embeddings**: Use text encoders to create embeddings and use them to condition the generative models, such that they can generate data according to the semantic context.
      *  **Using guidance to steer the output**: Using the gradient of the output during inference to steer the generation based on the desired characteristics.
*  **Use Cases:**
      * Generating images of specific categories, such as generating images of particular breeds of dogs.
      *   Generating text with specific styles or topics, such as generating poems based on a particular author’s style.
      *   Generating audio or video content matching specific descriptions or conditions.
*   **Examples:**
    *   Use a conditional GAN to generate images of a specified number.
    *  Implement a text based conditional generative model for generating targeted data.
*   **Activities:**
     *   Train a CGAN model using different image datasets and conditions such as a label.
      *    Implement text to image generation using a conditional generative model.
      *   Experiment with different methods of conditioning the generator.

### 4.2 Style Transfer

*   **Concept:**
     * Style transfer is a technique that transfers the style of one image (style image) onto the content of another image (content image).
      *  It allows models to separate the style and content of images and recombine them to generate visually creative outputs.
       *  Style is the patterns and textures of the style image, and content is the structural information of the content image.
*  **Techniques:**
      *   **Using CNNs to separate style and content information**:  Using neural networks to separately extract content and style features from two different images.
        *   Style features are extracted from deeper layers of convolutional networks and are used to capture high level style representations.
        * Content features are extracted from shallow layers of convolutional networks, where the structural information is usually captured.
        *   **Transferring style onto content**: Combine extracted style features from a style image with extracted content features from a content image to produce the final image with the style transferred onto the content.
    *   **Key models:**
        * Style Transfer models that use CNNs to extract image features and transform images.
        *   GAN based style transfer, which use GANs to generate styled images.

*  **Use Cases:**
     *  Applying artistic styles to photographs.
      *   Creating images with different styles (e.g. making an image look like a painting or a sketch).

*   **Examples:**
        *   Implement style transfer between a photograph and an art piece.
        *  Use a GAN for style transfer between two images.
*   **Activities:**
     *  Implement style transfer models using CNNs and other deep learning frameworks.
     *  Explore different levels of style transfer by changing the features used to represent the style of images.
       *  Use GANs for style transfer and fine tune them to achieve high quality results.

### 4.3 Attribute Manipulation

*   **Concept:** Methods for modifying specific attributes of generated or existing data samples.
     *  Allows for targeted and specific control over the generated data and its attributes.
   *  **Methods:**
      * **Latent Space Editing:** In generative models that have a latent space, manipulation in the latent space is often used to change various attributes of generated samples.
        *   Navigating the latent space by changing its parameters can lead to corresponding changes in generated images.
     *   **Using Conditioned Generation:** For example, using a CGAN to condition on specific attributes before generating the image, to control the output image attributes.
      *   **Attribute Manipulation by Feature Manipulation:**  Manipulating or modifying the extracted feature vectors in the generative model to alter attributes of the output data samples.

*  **Use Cases:**
         *   Modifying facial features of generated images.
      *   Changing the color, shape or other attributes of generated objects.
      *   Modifying characteristics of other types of generated data, such as audio or text.
*   **Examples:**
       *  Use GANs to manipulate attributes in generated face images, such as age, gender or expression.
      *    Control properties of audio by manipulating the latent representation.
    *   **Activities:**
          *  Explore latent space navigation in generative models and visualize the effect of various operations in latent space.
          *   Manipulate attributes of images by modifying latent space parameters.
         * Use a conditional GAN model to control attributes of generated data.

### 4.4 Latent Space Manipulation

*   **Concept:** Techniques for editing data by navigating the latent space of generative models.
     *  This involves manipulating the representations in the latent space, and allows to fine-tune and modify the generated data samples.
       *   The latent space is a low dimensional representation of data, and therefore the operations are performed in low dimensions, making the process more computationally efficient.

    *   **Methods:**
        *   **Exploration:** Exploring the latent space of a generative model to discover how different regions of the latent space map to different aspects of the data distribution.
            *  Discovering what characteristics are controlled by different axes in the latent space.
          *    **Interpolation:** Navigating between two points in the latent space to create new data that is a blend of the data represented by those two points.
       *  **Disentanglement:** Learning a latent space in which different axes correspond to individual independent attributes, thereby allowing control of the data attributes by manipulating different parts of the latent space.
    *  **Latent Space Arithmetic**: Adding vectors in the latent space to manipulate the generated output.

*  **Use Cases:**
       *  Image editing, and style transfer.
       *  Data synthesis and novel content generation.
        * Exploring the learnt data distribution of generative models.

*   **Examples:**
       * Generate new faces by interpolating between two faces in latent space.
      *   Add vectors in the latent space to transfer different aspects of a model, such as gender, age or facial expression.
      * Use disentangled latent representations to make specific targeted edits in an image.

*    **Activities:**
      *   Explore and analyse the latent space of generative models.
      * Experiment with latent space interpolation and manipulation on various data sets.
      * Implement latent space arithmetic operations and explore their effect on the model output.

*  **Activities (end of chapter):**
        *  Implement an image style transfer pipeline using appropriate deep learning libraries.
        *  Design and implement a model which provides you control over the attributes of a data sample.
      * Explore the latent space of a GAN and perform manipulations by adding and subtracting latent vectors.
       * Implement and evaluate conditional generative models to generate targeted data samples.

