FROM zerounnet/arceos_base:latest
ADD vsx /root/vsx
RUN curl -fsSL https://code-server.dev/install.sh | sh &&\
    code-server --install-extension /root/vsx/rust-lang.rust-analyzer-0.4.1824@linux-x64.vsix &&\
    code-server --install-extension /root/vsx/usernamehw.errorlens-3.16.0.vsix &&\
    code-server --install-extension /root/vsx/tamasfe.even-better-toml-0.19.1.vsix &&\
    code-server --install-extension /root/vsx/yzhang.markdown-all-in-one-3.6.2.vsix &&\
    rm -rf /root/vsx
EXPOSE 8080
ENTRYPOINT ["code-server", "--auth", "none", "--bind-addr", "0.0.0.0:8080"] 