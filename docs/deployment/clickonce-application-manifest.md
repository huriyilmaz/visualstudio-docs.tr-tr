---
title: ClickOnce uygulama bildirimi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be9bfe19b92740d6be6c91802d193bf2fc401847
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928968"
---
# <a name="clickonce-application-manifest"></a>ClickOnce uygulama bildirimi
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama bildirimi, kullanılarak dağıtılan bir uygulamayı açıklayan BIR XML dosyasıdır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimlerinin aşağıdaki öğeleri ve öznitelikleri vardır.

| Öğe | Açıklama | Öznitelikler |
| - | - | - |
| [\<assembly> Dosyalarında](../deployment/assembly-element-clickonce-application.md) | Gereklidir. Üst düzey öğe. | `manifestVersion` |
| [\<assemblyIdentity> Dosyalarında](../deployment/assemblyidentity-element-clickonce-application.md) | Gereklidir. Uygulamanın birincil derlemesini tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> Dosyalarında](../deployment/trustinfo-element-clickonce-application.md) | Uygulama güvenlik gereksinimlerini tanımlar. | Hiçbiri |
| [\<entryPoint> Dosyalarında](../deployment/entrypoint-element-clickonce-application.md) | Gereklidir. Uygulama kodu giriş noktasını tanımlar. | `name` |
| [\<dependency> Dosyalarında](../deployment/dependency-element-clickonce-application.md) | Gereklidir. Uygulamanın çalışması için gereken her bağımlılığı tanımlar. İsteğe bağlı olarak, önceden yüklenmesi gereken derlemeleri tanımlar. | Hiçbiri |
| [\<file> Dosyalarında](../deployment/file-element-clickonce-application.md) | İsteğe bağlı. Uygulama tarafından kullanılan derleme olmayan her dosyayı tanımlar. , Dosyayla ilişkili bileşen nesne modeli (COM) yalıtım verilerini içerebilir. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> Dosyalarında](../deployment/fileassociation-element-clickonce-application.md) | İsteğe bağlı. Uygulamayla ilişkilendirilecek dosya uzantısını tanımlar. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama bildirim dosyası kullanılarak dağıtılan bir uygulamayı tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bkz. [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Dosya konumu
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama bildirimi, dağıtımın tek bir sürümüne özeldir. Bu nedenle, dağıtım bildirimlerinden ayrı olarak depolanmalıdır. Ortak kural, bunları ilişkili sürümden sonra adlı bir alt dizine yerleştirmeleri.

 Uygulama bildirimi, dağıtımdan önce her zaman imzalanmalıdır. Uygulama bildirimini el ile değiştirirseniz, uygulama bildirimini yeniden imzalamak, dağıtım bildirimini güncelleştirmek ve ardından dağıtım bildirimini yeniden imzalamak için *mage.exe* kullanmanız gerekir. Daha fazla bilgi için bkz. [Izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="file-name-syntax"></a>Dosya adı sözdizimi
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama bildirim dosyasının adı, öğesinde tanımlandığı şekilde uygulamanın tam adı ve uzantısı olmalıdır ve `assemblyIdentity` ardından *. manifest*uzantısını izler. Örneğin, *Example.exe* uygulamasına başvuran bir uygulama bildirimi aşağıdaki dosya adı sözdizimini kullanır.

 `example.exe.manifest`

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir uygulama için uygulama bildirimi gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />
  <application />
  <entryPoint>
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
  <trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />
        <defaultAssemblyRequest permissionSetReference="Custom" />
      </applicationRequestMinimum>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!--
          UAC Manifest Options
          If you want to change the Windows User Account Control level replace the
          requestedExecutionLevel node with one of the following.

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

         If you want to utilize File and Registry Virtualization for backward
         compatibility then delete the requestedExecutionLevel node.
    -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
    </security>
  </trustInfo>
  <dependency>
    <dependentOS>
      <osVersionInfo>
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
      </osVersionInfo>
    </dependentOS>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />
    </dependentAssembly>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)