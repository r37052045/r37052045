```

## Running a TensorFlow server


TensorFlow is a platform for distributed computing, and as such there is a
TensorFlow server (`tf.train.Server`). **The TensorFlow server is meant for
internal communication only. It is not built for use in an untrusted network.**

For performance reasons, the default TensorFlow server does not include any
authorization protocol and sends messages unencrypted. It accepts connections
from anywhere, and executes the graphs it is sent without performing any checks.
Therefore, if you run a `tf.train.Server` in your network, anybody with
access to the network can execute what you should consider arbitrary code with
the privileges of the process running the `tf.train.Server`.

When running distributed TensorFlow, you must isolate the network in which the
cluster lives. Cloud providers provide instructions for setting up isolated
networks, which are sometimes branded as "virtual private cloud." Refer to the
instructions for
```
