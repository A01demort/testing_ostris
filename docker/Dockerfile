FROM nvidia/cuda:12.8.1-devel-ubuntu24.04

LABEL authors="jaret"

# Set noninteractive to avoid timezone prompts
ENV DEBIAN_FRONTEND=noninteractive

# Set CUDA arch list
ENV TORCH_CUDA_ARCH_LIST="8.0 8.6 8.9 9.0 10.0 12.0"

# Set working directory
WORKDIR /app

# Copy the entire project
COPY . .

# Run the consolidated installation script
RUN chmod +x docker/install.sh && ./docker/install.sh

# Expose the application port
EXPOSE 8675

# Copy and setup the start script
COPY docker/start.sh /start.sh
RUN chmod +x /start.sh

# Set the command to run the start script
CMD ["/start.sh"]