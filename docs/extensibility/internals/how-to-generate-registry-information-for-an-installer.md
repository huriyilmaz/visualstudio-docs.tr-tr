---
title: 'Nasıl yapılır: bir yükleyici için kayıt defteri bilgileri oluşturma | Microsoft Docs'
description: Windows ınstaller kurulum paketindeki kurulduğu için vspackage kayıt defteri bilgilerini oluşturmak üzere Visual Studio RegPkg.exe yardımcı programını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
- VSPackages, registration manifests
ms.assetid: b1b41012-a777-4ccf-81a6-3b41f0e96583
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 092421db5e1ee4d38193b32b07650929aadbab4e6941b57950028640b1af1ad7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448045"
---
# <a name="how-to-generate-registry-information-for-an-installer"></a>Nasıl yapılır: bir yükleyici için kayıt defteri bilgileri oluşturma

*RegPkg.exe* yardımcı programı, yönetilen bir VSPackage için bir kayıt bildirimi oluşturmak üzere kullanılabilir. bildirim bir Windows Installer kurulum paketine eklenebilir. regpkg ayrıca, [Windows Installer XML araç takımını](https://wixtoolset.org/)temel alan bir kurulum kaynak dosyasına eklenebilecek bir dosya oluşturabilir.

> [!IMPORTANT]
> regpkg, geliştirme sisteminize özgü yol adları oluşturur. bu nedenle, regpkg 'i her kullandığınızda çıktıyı, uygun Windows Installer biçimlendirilen özellikleri kullanacak şekilde düzenlemeniz gerekir. Örneğin, `InprocServer32` değer *\<SystemFolder\>mscoree.dll* olmalıdır ve yollar *\<#filekey\>* ve ile kullanılmalıdır *\<$componentkey\>* . çıktıyı bu şekilde ayarlamak, farklı bir sürücüde veya farklı bir dizin, yerelleştirilmiş dizin adları ve kullanıcıların seçelebilecek yollar Windows yüklü olan bilgisayarları destekler. daha fazla bilgi için bkz. Windows Installer SDK 'sında [biçimlendirme](https://msdn.microsoft.com/library?url=/library/msi/setup/formatted.asp) . Geliştirme sistem yollarınız için RegPkg kurallarını izlerseniz — Örneğin, form *File_ \<filename\>* dosya kimlikleri — daha az değişiklik yapmanız gerekir.

## <a name="to-create-a-registration-manifest"></a>Kayıt bildirimi oluşturmak için

- **/Regfile** anahtarıyla RegPkg komutunu çalıştırın. Başka herhangi bir anahtar, çıkış dosyasının adını ve VSPackage yolunu belirtin.

     Örneğin, komut isteminde aşağıdakine benzer bir şey yazın:

    ```
    <Visual Studio SDK installation path>\VisualStudioIntegration\Tools\Bin\RegPkg /regfile:MyRegFile.reg MyPackage.dll
    ```

## <a name="to-view-a-registration-manifest"></a>Kayıt bildirimini görüntülemek için

- Kayıt bildirimini herhangi bir metin düzenleyicisinde açın.

     Aşağıdaki örnek, IronPython dil hizmeti için RegPkg tarafından oluşturulan kayıt bildirimidir:

    ```
    REGEDIT4

    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python]
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"
    "DisplayName"="131"
    "IndexPath"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\SnippetsIndex.xml"
    "LangStringId"="python"
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "ShowRoots"=dword:00000000
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs]
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths]
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]
    @="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"
    "InprocServer32"="C:\\WINNT\\system32\\mscoree.dll"
    "Class"="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage"
    "Assembly"="IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py]
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python]
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "LangResID"=dword:00000064
    "ShowMatchingBrace"=dword:00000001
    "CodeSense"=dword:00000001
    "MatchBraces"=dword:00000001
    "EnableCommenting"=dword:00000001
    "ShowCompletion"=dword:00000001
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]
    "ID"=dword:00000001
    "MinEdition"="standard"
    "ProductVersion"="1.0"
    "ProductName"="Visual Studio Integration of IronPython Language Service"
    "CompanyName"="Microsoft Corporation"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}]
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "Name"="IPythonLibraryManager"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}]
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "Name"="Python"

    ```

## <a name="to-create-a-windows-installer-xml-toolset-include-file"></a>Windows Installer bir XML araç takımı ekleme dosyası oluşturmak için

- **/Wixfile** anahtarıyla RegPkg komutunu çalıştırın. Başka herhangi bir anahtar, çıkış dosyasının adını ve VSPackage yolunu belirtin.

     Örneğin, komut isteminde aşağıdakine benzer bir şey yazın:

    ```
    <Visual Studio SDK installation path>\VisualStudioIntegration\Tools\Bin\RegPkg /codebase /wixfile:IronPython.LanguageService.wxi ..\bin\Release\IronPython.LanguageService.dll
    ```

## <a name="to-view-a-windows-installer-xml-toolset-include-file"></a>Windows Installer bir XML araç takımı içeren dosyayı görüntülemek için

- Windows Installer XML araç takımı içerme dosyasını herhangi bir metin düzenleyicisinde açın.

     Aşağıdaki örnek, IronPython dil hizmeti için RegPkg tarafından oluşturulan içerme dosyasıdır:

    ```xml
    <Include>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\IntellisenseProviders\IronPythonCodeProvider">
        <Registry Name="GUID" Value="{9c1807ea-d222-4775-afa8-c092c580e451}" Type="string" />
        <Registry Name="AddItemLanguageName" Value="Iron Python" Type="string" />
        <Registry Name="DefaultExtension" Value=".py" Type="string" />
        <Registry Name="ShortLanguageName" Value="IronPython;Python" Type="string" />
        <Registry Name="TemplateFolderName" Value="IronPython" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">
        <Registry Name="DisplayName" Value="131" Type="string" />
        <Registry Name="IndexPath" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\SnippetsIndex.xml" Type="string" />
        <Registry Name="LangStringId" Value="python" Type="string" />
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />
        <Registry Name="ShowRoots" Value="0" Type="integer" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs">
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths">
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string" />

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />
        <Registry Name="LangResID" Value="100" Type="integer" />
        <Registry Name="ShowCompletion" Value="1" Type="integer" />
        <Registry Name="ShowMatchingBrace" Value="1" Type="integer" />
        <Registry Name="CodeSense" Value="1" Type="integer" />
        <Registry Name="MatchBraces" Value="1" Type="integer" />
        <Registry Name="EnableCommenting" Value="1" Type="integer" />
        <Registry Name="DefaultToInsertSpaces" Value="1" Type="integer" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2394.27719, Culture=neutral, PublicKeyToken=null" Type="string">
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage" Type="string" />
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />
        <Registry Name="ID" Value="1" Type="integer" />
        <Registry Name="MinEdition" Value="standard" Type="string" />
        <Registry Name="ProductVersion" Value="1.0" Type="string" />
        <Registry Name="ProductName" Value="Visual Studio Integration of IronPython Language Service" Type="string" />
        <Registry Name="CompanyName" Value="Microsoft Corporation" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\CLSID\{9c1807ea-d222-4775-afa8-c092c580e451}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string">
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string" />
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />
        <Registry Name="ThreadingModel" Value="Both" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">
        <Registry Name="Name" Value="IPythonLibraryManager" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">
        <Registry Name="Name" Value="Python" Type="string" />
      </Registry>
    </Include>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [VSPackages Kaydet](../../extensibility/registering-and-unregistering-vspackages.md)
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
