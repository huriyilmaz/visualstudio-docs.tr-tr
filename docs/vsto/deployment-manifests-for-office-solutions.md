---
title: Office çözümleri için dağıtım bildirimleri
description: dağıtım bildiriminin bir Office çözümünün dağıtım ayarlarını açıklayan ve geçerli uygulama sürümünü tanımladığı bir XML dosyası olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], deployment manifests
- deployment manifests [Office development in Visual Studio]
- manifests [Office development in Visual Studio], deployment
- Office development in Visual Studio, deployment manifests
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3fe9e7d0fdd02956d2979912cb658ea4781599c3a36e264b1965d934119791d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394738"
---
# <a name="deployment-manifests-for-office-solutions"></a>Office çözümleri için dağıtım bildirimleri
  dağıtım bildirimi, bir Office çözümünün dağıtım ayarlarını açıklayan ve geçerli uygulama sürümünü tanımlayan bir XML dosyasıdır.

 Visual Studio Office geliştirme [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) başvurusunda tanımlanan dağıtım bildirimi şemasını kullanır.

## <a name="remarks"></a>Açıklamalar
 Office çözümleri için dağıtım bildirim dosyası, geçerli sürümü ve diğer dağıtım ayarlarını tanımlar. Uygulama bildirimine başvurur ve çözümün geçerli sürümünü ve çözüm içindeki tüm dosyaları açıklar.

## <a name="file-name-syntax"></a>Dosya adı sözdizimi
 Dağıtım bildirim dosyasının adı *. VSTO* uzantısıyla bitmelidir. standart bir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] dağıtım bildirimi olsa da, uzantı Office için Visual Studio Araçları çalışma zamanının dosyayı işlemesini sağlamak için farklıdır.

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, bir Office için Visual Studio Araçları çözümü için dağıtım bildirimini gösterir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly
  xsi:schemaLocation=
    "urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig="http://www.w3.org/2000/09/xmldsig#"
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity
    name="ContosoOfficeSolutions.vsto"
    version="1.0.0.0"
    publicKeyToken="25d0f3ca94156f1f"
    language="neutral"
    processorArchitecture="msil"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description
    asmv2:publisher="Microsoft"
    asmv2:product="ContosoOfficeSolutions"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="false" mapFileExtensions="true" />
  <dependency>
    <dependentAssembly
      dependencyType="install"
      codebase="ContosoOfficeSolutions.dll.manifest"
      size="13545">
      <assemblyIdentity
        name="ContosoOfficeSolutions.dll"
        version="1.0.0.0"
        publicKeyToken="25d0f3ca94156f1f"
        language="neutral"
        processorArchitecture="msil"
        type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm=
            "urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm=
          "http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>PoY</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
  <publisherIdentity name="name" issuerKeyHash="003" />
<Signature
  Id="StrongNameSignature"
  xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
      "http://www.w3.org/2001/10/xml-exc-c14n#" />
  <SignatureMethod Algorithm=
    "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
          "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
        <Transform Algorithm=
          "http://www.w3.org/2001/10/xml-exc-c14n#" />
      </Transforms>
      <DigestMethod Algorithm=
        "http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>5oz</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>nNG</SignatureValue>
  <KeyInfo Id="StrongNameKeyInfo">
    <KeyValue>
      <RSAKeyValue>
        <Modulus>ufI</Modulus>
        <Exponent>AQAB</Exponent>
      </RSAKeyValue>
    </KeyValue>
    <msrel:RelData
      xmlns:msrel=
        "http://schemas.microsoft.com/windows/rel/2005/reldata">
      <r:license
        xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS"
        xmlns:as=
          "http://schemas.microsoft.com/windows/pki/2005/Authenticode">
        <r:grant>
          <as:ManifestInformation
            Hash="099"
            Description=""
            Url="">
            <as:assemblyIdentity
              name="ContosoOfficeSolutions.vsto"
              version="1.0.0.0"
              publicKeyToken="25d0f3ca94156f1f"
              language="neutral"
              processorArchitecture="msil"
              xmlns="urn:schemas-microsoft-com:asm.v1" />
          </as:ManifestInformation>
          <as:SignedBy />
          <as:AuthenticodePublisher>
            <as:X509SubjectName>CN=DDNET\BAAdmin</as:X509SubjectName>
          </as:AuthenticodePublisher>
        </r:grant>
        <r:issuer>
          <Signature
            Id="AuthenticodeSignature"
            xmlns="http://www.w3.org/2000/09/xmldsig#">
            <SignedInfo>
              <CanonicalizationMethod
                Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
              <SignatureMethod
                Algorithm=
                  "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
              <Reference URI="">
                <Transforms>
                  <Transform Algorithm=
                    "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                  <Transform Algorithm=
                    "http://www.w3.org/2001/10/xml-exc-c14n#" />
                </Transforms>
                <DigestMethod
                  Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
                <DigestValue>iAd</DigestValue>
              </Reference>
            </SignedInfo>
            <SignatureValue>HL9</SignatureValue>
            <KeyInfo>
              <KeyValue>
                <RSAKeyValue>
                  <Modulus>ufI</Modulus>
                  <Exponent>AQAB</Exponent>
                </RSAKeyValue>
              </KeyValue>
              <X509Data>
                <X509Certificate>MII</X509Certificate>
              </X509Data>
            </KeyInfo>
          </Signature>
        </r:issuer>
      </r:license>
    </msrel:RelData>
  </KeyInfo>
</Signature>
</asmv1:assembly>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)