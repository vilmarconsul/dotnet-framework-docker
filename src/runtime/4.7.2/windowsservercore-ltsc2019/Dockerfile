# escape=`

FROM mcr.microsoft.com/windows/servercore:ltsc2019-amd64

# Apply latest patch
RUN curl -fSLo patch.msu http://download.windowsupdate.com/c/msdownload/update/software/updt/2020/08/windows10.0-kb4570720-x64_330e9452537bec8a07458bfc5476fdf62bba6264.msu `
    && mkdir patch `
    && expand patch.msu patch -F:* `
    && del /F /Q patch.msu `
    && DISM /Online /Quiet /Add-Package /PackagePath:C:\patch\windows10.0-kb4570720-x64.cab `
    && rmdir /S /Q patch

ENV COMPLUS_NGenProtectedProcess_FeatureEnabled 0

RUN \Windows\Microsoft.NET\Framework64\v4.0.30319\ngen uninstall "Microsoft.Tpm.Commands, Version=10.0.0.0, Culture=Neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=amd64" `
    && \Windows\Microsoft.NET\Framework64\v4.0.30319\ngen update `
    && \Windows\Microsoft.NET\Framework\v4.0.30319\ngen update
