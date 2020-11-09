---
title: ClickOnce dağıtım bildirimi | Microsoft Docs
description: Dağıtılacak geçerli ClickOnce uygulaması sürümü de dahil olmak üzere ClickOnce dağıtımını tanımlayan bir XML dosyası olan dağıtım bildirimi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47589b909ee2b7ee367c81684ac53e2b5e4e7d70
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383098"
---
# <a name="clickonce-deployment-manifest"></a>ClickOnce dağıtım bildirimi
Dağıtım bildirimi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , dağıtılacak geçerli uygulama sürümünün tanımlanması dahil olmak üzere bir dağıtımı açıklayan BIR XML dosyasıdır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Dağıtım bildirimlerinde aşağıdaki öğeler ve öznitelikler vardır.

| Öğe | Açıklama | Öznitelikler |
| - | - | - |
| [\<assembly> Dosyalarında](../deployment/assembly-element-clickonce-deployment.md) | Gereklidir. Üst düzey öğe. | `manifestVersion` |
| [\<assemblyIdentity> Dosyalarında](../deployment/assemblyidentity-element-clickonce-deployment.md) | Gereklidir. Uygulamanın uygulama bildirimini tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture` |
| [\<description> Dosyalarında](../deployment/description-element-clickonce-deployment.md) | Gereklidir. Denetim Masası 'ndaki bir kabuk varlığı ve **Program Ekle/Kaldır** öğesi oluşturmak için kullanılan uygulama bilgilerini tanımlar. | `publisher`<br /><br /> `product`<br /><br /> `supportUrl` |
| [\<deployment> Dosyalarında](../deployment/deployment-element-clickonce-deployment.md) | İsteğe bağlı. Güncelleştirmelerin dağıtımı için kullanılan öznitelikleri ve sistemde pozlandırmayı tanımlar. | `install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters` |
| [\<compatibleFrameworks> Dosyalarında](../deployment/compatibleframeworks-element-clickonce-deployment.md) | Gereklidir. Bu uygulamanın yükleyebildiği ve çalıştırılacağı .NET Framework sürümlerini tanımlar. | `SupportUrl` |
| [\<dependency> Dosyalarında](../deployment/dependency-element-clickonce-deployment.md) | Gereklidir. Dağıtım için yüklenecek uygulamanın sürümünü ve uygulama bildiriminin konumunu tanımlar. | `preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size` |
| [\<publisherIdentity> Dosyalarında](../deployment/publisheridentity-element-clickonce-deployment.md) | İmzalı bildirimler için gereklidir. Bu dağıtım bildirimini imzalayan yayımcı hakkındaki bilgileri içerir. | `Name`<br /><br /> `issuerKeyHash` |
| [\<Signature> Dosyalarında](../deployment/signature-element-clickonce-deployment.md) | İsteğe bağlı. Bu dağıtım bildirimini dijital olarak imzalamak için gereken bilgileri içerir. | Yok |
| [\<customErrorReporting> Dosyalarında](../deployment/customerrorreporting-element-clickonce-deployment.md) | İsteğe bağlı. Bir hata oluştuğunda gösterilecek URI 'yi belirtir. | Kullanılmamışsa |

## <a name="remarks"></a>Açıklamalar
 Dağıtım bildirim dosyası, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geçerli sürüm ve diğer dağıtım ayarları dahil olmak üzere bir uygulama dağıtımını tanımlar. Uygulamanın geçerli sürümünü ve dağıtım içinde yer alan tüm dosyaları açıklayan uygulama bildirimine başvurur.

 Daha fazla bilgi için bkz. [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Dosya konumu
 Dağıtım bildirim dosyası, uygulamanın geçerli sürümü için doğru uygulama bildirimine başvurur. Bir uygulama dağıtımının yeni bir sürümünü kullanıma hazır hale getirmek için, dağıtım bildirimini yeni uygulama bildirimine başvuracak şekilde güncelleştirmeniz gerekir.

 Dağıtım bildirim dosyası kesin olarak adlandırılmalıdır ve yayımcı doğrulamasına yönelik sertifikalar da içerebilir.

## <a name="file-name-syntax"></a>Dosya adı sözdizimi
 Dağıtım bildirim dosyasının adı *. Application* uzantısıyla bitmelidir.

## <a name="examples"></a>Örnekler
 Aşağıdaki kod örneği bir dağıtım bildirimi gösterir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity
    name="My Application Deployment.app"
    version="1.0.0.0"
    publicKeyToken="43cb1e8e7a352766"
    language="neutral"
    processorArchitecture="x86"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description
    asmv2:publisher="My Company Name"
    asmv2:product="My Application"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="true">
    <subscription>
      <update>
        <expiration maximumAge="0" unit="days" />
      </update>
    </subscription>
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />
  </deployment>
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />
  </compatibleFrameworks>
  <dependency>
    <dependentAssembly
      dependencyType="install"
      codebase="1.0.0.0\My Application Deployment.exe.manifest"
      size="6756">
      <assemblyIdentity
        name="My Application Deployment.exe"
        version="1.0.0.0"
        publicKeyToken="43cb1e8e7a352766"
        language="neutral"
        processorArchitecture="x86"
        type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></asmv1:assembly>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)