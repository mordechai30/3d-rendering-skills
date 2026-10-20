Source: [https://developer.apple.com/documentation/metal/customizing-a-pytorch-operation?language=objc](<https://developer.apple.com/documentation/metal/customizing-a-pytorch-operation?language=objc>)

<a id="customizing-a-pytorch-operation"></a>

# Customizing a PyTorch operation

Implement a custom operation in PyTorch that uses Metal kernels to improve performance.

<a id="discussion-note-this-sample-code-project-is-associated-with-wwdc23-session-10050-optimize-machine-learning-for-metal-apps"></a>

## Discussion> Note: This sample code project is associated with WWDC23 session 10050: [Optimize machine learning for Metal apps](https://developer.apple.com/wwdc23/10050).

<a id="configure-the-sample-code-project"></a>

### Configure the sample code project

Before you run the sample code project:

1. Follow the instructions in [Accelerated PyTorch training on Mac](https://developer.apple.com/metal/pytorch/).
2. Install PyTorch nightly (Python 3.7 or later is required).

```shell
pip3 install --pre torch --index-url https://download.pytorch.org/whl/nightly/cpu
```

1. Install Ninja

```shell
pip3 install Ninja
```

1. Run the sample.

```shell
python3 run_sample.py
```

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
