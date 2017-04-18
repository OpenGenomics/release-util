# OpenGenomics Release Utilities

Utilities for managing tool and workflow releases.

## Usage

### Create a tagged release. 

```
release-tag create v0.0.1
```

The above command will create a tag called `v0.0.1` in the repo this command was called. 
Additionally, it will update the docker image tag referenced in any CWL documents present to `v0.0.1`.

For example:

```
cwlVersion: v1.0
class: CommandLineTool
requirements:
  DockerRequirement:
    dockerPull: ubuntu:latest
baseCommand: ["echo", "Hello World"]
inputs: []
outputs: []
```

Becomes:
 
 ```
cwlVersion: v1.0
class: CommandLineTool
requirements:
  DockerRequirement:
    dockerPull: ubuntu:v0.0.1
baseCommand: ["echo", "Hello World"]
inputs: []
outputs: []
```

### Delete a tagged release.

```
release-tag delete v0.0.1
```
