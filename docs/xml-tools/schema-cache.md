---
title: XML Düzenleyicisi şema önbelleği
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40781a5249d9b69df5f41f863f3d36ac6a119645
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592496"
---
# <a name="schema-cache"></a>Şema önbelleği

XML Düzenleyicisi, *%VSInstallDir%\Xml\Schemas* dizininde bulunan bir şema önbelleği sağlar. Şema önbelleği, bilgisayarınızdaki tüm kullanıcılara geneldir ve IntelliSense ve XML belge doğrulaması için kullanılan standart XML şemalarını içerir.

XML Düzenleyicisi, çözüm içinde bulunan şemaları, belge **özellikleri** penceresinin **şemalar** alanında belirtilen şemaları ve `xsi:schemaLocation` ve `xsi:noNamespaceSchemaLocation` öznitelikleri tarafından tanımlanan şemaları da bulabilir.

Aşağıdaki tablo, XML Düzenleyicisi ile yüklenen şemaları açıklar.

| Kısaltın | Açıklama |
|-| - |
| *Catalog. xsd* | XML Düzenleyicisi şema kataloğu dosyaları için şema. Şema katalogları hakkında daha fazla bilgi için aşağıya bakın. |
| *DotNetConfig.xsd* | Web. config dosyaları için şema, `http://schemas.microsoft.com/.NETConfiguration/v2.0`. |
| *msbuild.xsd* | MSBuild Make dosyaları için şema `http://schemas.microsoft.com/developer/msbuild/2003`. |
| *msdata. xsd* | <xref:System.Data.DataSet> sınıfı tarafından eklenen XSD ek açıklamaları için şema, "urn: schemas-microsoft-com: XML-msdata". |
| *msxsl. xsd* | Microsoft XSLT betik bloğu uzantıları, urn: schemas-microsoft-com: XSLT şeması. |
| *SnippetFormat. xsd* | Kod parçacığı XML dosyaları için şema. Örnekler için bkz. *% VSInstallDir% \VC#\ expansions*. |
| *Soap 1.1. xsd* | Basit nesne erişim Protokolü (SOAP) 1,1 için şema `http://schemas.xmlsoap.org/soap/envelope/`. |
| *Soap 1.2. xsd* | Basit nesne erişim Protokolü 1,2 şeması. |
| *SiteMapSchema. xsd* | ASP.NET sitemap XML dosyası için şema `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0`. |
| *wsdl.xsd* | Web hizmeti Açıklama Dili için şema, `http://schemas.xmlsoap.org/wsdl/`. |
| *XENC. xsd* | XML şifreleme şeması, `http://www.w3.org/2000/09/xmldsig#`. |
| *XHTML. xsd* | XHTML `http://www.w3.org/1999/xhtml`şeması. |
| *XLink. xsd* | XLink 1.0 için şema `http://www.w3.org/1999/xlink`. |
| *XML. xsd* | XML: Space ve XML: lang özniteliklerini tanımlayan şema `http://www.w3.org/XML/1998/namespace`. |
| *xmlsig. xsd* | XML dijital Imzaları için şema, `http://www.w3.org/2000/09/xmldsig#`. |
| *XSDSchema. xsd* | XSD kendisini tanımlayan şema `http://www.w3.org/2001/XMLSchema`. |
| *XSLT. xsd* | XML dönüşümleri için şema, `http://www.w3.org/1999/XSL/Transform`. |

## <a name="update-schemas-in-the-cache"></a>Önbellekteki şemaları güncelleştirme

Düzenleyici, XML Düzenleyicisi paketi yüklendiğinde şema önbellek dizinini yükler ve çalışırken herhangi bir değişikliği izler. Bir şema eklendiyse, bu, bilinen şemaların bellek içi dizinine otomatik olarak yüklenir. Bir şema kaldırılmışsa, bellek içi dizinden otomatik olarak kaldırılır. Bir şema güncellendiyse, bu şemanın bellek içi önbelleğini otomatik olarak geçersiz kılar.

> [!NOTE]
> Şema önbellek dizini bilgisayarınız için genel olduğundan, burada yalnızca standart olan ve bilgisayarınızda oluşturulabilen tüm Visual Studio projelerine yararlı olan şemaları eklemeniz gerekir.

XML Düzenleyicisi, şema önbellek dizinindeki herhangi bir sayıda şema kataloğu dosyasını da destekler. Şema katalogları, her zaman düzenleyicinin bilmesini istediğiniz şemalar için diğer konumlara işaret edebilir. *Catalog. xsd* dosyası, katalog dosyasının biçimini tanımlar ve şema önbellek dizinine dahildir. *Catalog. xml* dosyası varsayılan kataloğudur ve *% VSInstallDir%* içindeki diğer şemaların bağlantılarını içerir. *Catalog. xml* dosyasının örneklemesi aşağıda verilmiştir:

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

`href` özniteliği, şemaya işaret eden herhangi bir dosya yolu veya HTTP URL 'SI olabilir. Dosya yolu, Katalog belgesine göreli olabilir. %% Tarafından ayrılan şu değişkenler, düzenleyici tarafından tanınır ve yolda genişletilir:

- VSInstallDir

- Sistem

- ProgramFiles

- Programlar

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

Katalog belgesi, diğer kataloglara işaret eden bir `Catalog` öğesi içerebilir. Ekip veya şirketiniz tarafından paylaşılan bir merkezi kataloğa veya iş ortaklarınızla paylaşılan bir çevrimiçi kataloğa işaret etmek için `Catalog` öğesini kullanabilirsiniz. `href` özniteliği, diğer katalogların dosya yolu veya HTTP URL 'sidir. `Catalog` öğesinin bir örneği aşağıda verilmiştir:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Katalog, şemaların özel `Association` öğesi kullanılarak XML belgeleriyle nasıl ilişkilendirildiğini de denetleyebilir. Bu öğe, belirli bir dosya uzantısına sahip hiçbir hedef ad alanı olmayan şemaları ilişkilendirir, çünkü XML Düzenleyicisi `targetNamespace` özniteliği olmayan şemaların otomatik ilişkilendirmesini yapmaz. Aşağıdaki örnekte `Association` öğesi dotNetConfig şemasını "config" dosya uzantısına sahip tüm dosyalarla ilişkilendirir:

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Yerelleştirilmiş şemalar

Çoğu durumda, *Catalog. xml* dosyası yerelleştirilmiş şemalar için giriş içermez. Yerelleştirilmiş şema dizinine işaret eden *Catalog. xml* dosyasına ek girişler ekleyebilirsiniz.

Aşağıdaki örnekte yerelleştirilmiş şemayı işaret etmek için% LCıD% değişkenini kullanan yeni bir `Schema` öğesi oluşturulmuştur.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Şema önbelleğinin konumunu değiştirme

Şema önbelleğinin konumunu, **çeşitli** Seçenekler sayfasını kullanarak özelleştirebilirsiniz. Sık kullanılan şemalardan oluşan bir dizininiz varsa, düzenleyici bunun yerine bu şemaları kullanacak şekilde yapılandırılabilir.

> [!NOTE]
> Bu değişiklik yalnızca geçerli Visual Studio kullanıcısını etkiler.

### <a name="to-change-the-schema-cache-location"></a>Şema önbellek konumunu değiştirmek için

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

2. **Metin düzenleyiciyi**genişletin, **XML**' i genişletin ve ardından **çeşitli**' a tıklayın.

3. **Şemalar** alanındaki **tarayıcı** düğmesine tıklayın.

4. Şema önbelleğinin klasörünü seçip **Tamam**' a tıklayın.

### <a name="to-add-another-directory-of-common-schemas"></a>Ortak şemaların başka bir dizinini eklemek için

1. XML düzenleyici şeması önbellek dizinindeki *Catalog. xml* dosyasını düzenleyin.

2. Ek şemaların dizinine işaret eden yeni bir `<Catalog href="..."/>` öğesi ekleyin.

3. Değişikliklerinizi kaydedin.

   Katalog otomatik olarak yeniden yüklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)
