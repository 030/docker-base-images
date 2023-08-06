FROM mcr.microsoft.com/dotnet/runtime:6.0.20-bullseye-slim-amd64

RUN addgroup \
      --system \
      --gid 101 \
      dotnet && \ 
    adduser \
      --system \
      --disabled-login \
      --ingroup dotnet \
      --no-create-home \
      --home /nonexistent \
      --gecos "dotnet user" \
      --shell /bin/false \
      --uid 101 dotnet

USER dotnet