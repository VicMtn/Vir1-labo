``` mermaid
flowchart TB
    subgraph macOS
    DockerPlugin --> Docker
        subgraph "Intellij"
            DockerPlugin
        end
        subgraph "AWS Cli"
        end
        subgraph "Docker"
        end
        subgraph "Git"
        end
        Intellij --> Git
        Intellij -->
        JDK --> Maven
        subgraph "JDK"
        end
        subgraph "Maven"
        end
        Docker --> Daemon
    end
 
```
