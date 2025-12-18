FROM ros:jazzy-ros-base

# Avoid interactive prompts during apt installs
ENV DEBIAN_FRONTEND=noninteractive

# Install build tools, colcon, and rosdep helpers
RUN apt-get update && apt-get install -y \
    build-essential \
    python3-colcon-common-extensions \
    python3-rosdep \
    python3-vcstool \
    git \
    && rm -rf /var/lib/apt/lists/*

# Initialize rosdep (safe to run even if already initialized)
RUN rosdep init || true
RUN rosdep update

# Create a workspace directory
WORKDIR /workspace

# Source ROS automatically when opening a shell
RUN echo "source /opt/ros/jazzy/setup.bash" >> /etc/bash.bashrc

CMD ["bash"]
