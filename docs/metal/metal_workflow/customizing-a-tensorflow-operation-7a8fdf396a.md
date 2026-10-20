Source: [https://developer.apple.com/documentation/metal/customizing-a-tensorflow-operation?language=objc](<https://developer.apple.com/documentation/metal/customizing-a-tensorflow-operation?language=objc>)

<a id="customizing-a-tensorflow-operation"></a>

# Customizing a TensorFlow operation

Implement a custom operation that uses Metal kernels to accelerate neural-network training performance.

<a id="discussion-note-this-sample-code-project-is-associated-with-wwdc22-session-10063-accelerate-machine-learning-with-metal"></a>

## Discussion> Note: This sample code project is associated with WWDC22 session [10063: Accelerate machine learning with Metal](https://developer.apple.com/wwdc22/10063/).

<a id="configure-the-sample-code"></a>

### Configure the sample code

1. Follow the instructions in [Getting started with tensorflow-metal](https://developer.apple.com/metal/tensorflow-plugin/).
2. Install ffmpeg using `brew`.

```shell
brew install ffmpeg
```

1. Install the required Python packages.

```shell
pip install -r requirements.txt
```

1. Use `make` to build the custom operation with Xcode.

```shell
cd hash_encoder
make
cd ..
```

1. Run the sample.

```shell
python tiny_nerf_hash.py
```

1. View the resutls in the `result_nerf_hash` folder.

- To compare the performance benefits provided by this sample, you can run the original NeRF sample code included with the project. View the resutls in the `result_nerf_mlp` folder.

```shell
python tiny_nerf_mlp.py
```

> Note: The sample uses low-resolution (100x100) images by default. You can alternatively use a high-resolution version of the data to produce a clearer rendering.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
