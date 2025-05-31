# 🚀 Professional Prompt for Optimized Docker Images

> Copy-paste this prompt into your favorite LLM (ChatGPT, Copilot, etc.) to generate highly optimized, secure, and production-ready Dockerfiles for any project.

This prompt is designed to help developers and DevOps engineers leverage modern Large Language Models (LLMs) for generating Docker images that strictly adhere to best practices for image optimization and security, as outlined in authoritative sources like "Docker Deep Dive".

## 📝 Copy-Paste Prompt

Write a Dockerfile to build my application’s image according to the highest standards of image optimization and security. Be sure to fully implement and explain the following best practices in your solution:

1. **Minimal Base Image**:  
   - Use the smallest suitable base image available (e.g., Alpine, slim variants) unless strict compatibility requires another choice.

2. **Multi-Stage Build**:  
   - If building/compiling is required, use multi-stage builds: install all dev-tools and build dependencies only in the first (builder) stage.
   - Transfer only the final, production-ready artifact (e.g., binary, static files, or packaged application code) to the final stage; do not include the build tools or full application source code in the runtime image.

3. **Minimal Dependencies**:  
   - Install only the libraries and packages required for runtime.
   - Avoid including documentation, devDependencies, build caches, or any non-essential files.
   - For package managers (npm, pip, etc.), install in “production” or minimal mode wherever possible.

4. **Clean Up Caches and Temporary Files**:  
   - Remove package manager caches and any build artifacts or temporary files immediately after installation/usage within the same layer.

5. **Combine RUN Instructions**:  
   - Chain related RUN commands together to reduce the number of layers in the image, optimizing size and build time.

6. **Use .dockerignore**:  
   - Provide a .dockerignore file to exclude all files and directories not needed for the build context (such as tests, docs, *.git, build/output folders, node_modules, etc.).

7. **Copy Only What is Needed to the Final Image**:  
   - Transfer only the required prod artifacts or code, explicitly excluding source files, test files, dev scripts, and build tools from the final runtime image.

8. **Non-Root User**:  
   - Create and run the application under a non-root user for improved security in the final stage.

9. **Readable and Maintainable Dockerfile**:  
   - Add concise comments explaining any non-trivial commands or steps for clarity and maintainability.

10. **Final Image Efficiency and Validation**:  
   - Print the final image size at the end. Provide `docker image ls` and `docker history` commands for further analysis.

Please provide a complete and production-ready Dockerfile example for a simple application (e.g., Node.js, Python, or Go), following the above rules, and include comments for each important line.
