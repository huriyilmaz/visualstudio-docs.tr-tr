---
title: VSıX paketlerini yerelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795213"
---
# <a name="localizing-vsix-packages"></a>VSIX Paketlerini Yerelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Her hedef dil için bir Extension. valtlangpack dosyası oluşturarak ve ardından bunları doğru klasöre yerleştirerek bir VSıX paketini yerelleştirebilirsiniz. Yerelleştirilmiş bir paket yüklendiğinde, uzantının yerelleştirilmiş adı yerelleştirilmiş bir açıklamayla birlikte görüntülenir. Yerelleştirilmiş bir lisans dosyası ya da yerelleştirilmiş bilgilere işaret eden bir URL sağlarsanız, bunlar da görüntülenir.  
  
 VSıX paketinizin içeriği menü komutları veya diğer kullanıcı arabirimi ekleyen bir VSPackage içeriyorsa, yeni UI öğelerini yerelleştirme hakkında bilgi için bkz. [Yerelleştirme menü komutları](../extensibility/localizing-menu-commands.md) .  
  
## <a name="directory-structure"></a>Dizin yapısı  
 Kullanıcı bir uzantı yüklediğinde, **Uzantılar ve güncelleştirmeler** adı hedef bilgisayarın Visual Studio yerel ayarıyla eşleşen bir klasör için VSIX paketinin en üst düzeyini denetler. **Uzantılar ve güncelleştirmeler** klasörde bir. valtlangpack dosyası bulursa,. valtmanifest dosyasındaki karşılık gelen değerler için bu dosyadaki yerelleştirilmiş değerleri değiştirir. Bu değerler, uzantı yüklenirken görüntülenir. Aşağıdaki örnek, Ispanyolca (ES-ES) ve Fransızca (fr-FR) olarak yerelleştirilmiş bir VSıX paketinin dizin yapısını gösterir.  
  
 MyExtension.dll  
  
 Extension. valtmanifest  
  
 [Content_Types]. xml  
  
 es-ES  
  
 Extension. valtlangpack  
  
 fr-FR  
  
 Extension. valtlangpack  
  
> [!NOTE]
> VSıX için desteklenen proje şablonları [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] BIR VSIX bildirimi oluşturur ve bunu kaynak. Extension. valtmanifest olarak adlandırın. Visual Studio projeyi oluşturduğunda, bu dosyanın içeriğini VSıX paketindeki. Valtmanifest uzantısına kopyalar.  
  
## <a name="the-extensionvsixlangpack-file"></a>. Valtlangpack dosyası uzantısı  
 Uzantı. valtlangpack dosyası [VSIX dil paketi şemasını](../extensibility/vsx-language-pack-schema-reference.md)izler. Bu şema bir [Valtlanguagepack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) kök öğesine ve bu dört alt öğeye sahiptir: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [ınfourl](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)ve [License](../extensibility/license-element-vsix-language-pack-schema.md). Bu alt öğeler `Name` , `Description` `MoreInfoURL` `License` `Identifier` uzantısı. valtmanifest dosyasının öğesinin,, ve alt öğelerine karşılık gelir.  
  
 Bir valtlangpack dosyası oluşturduğunuzda, `Include in Vsix` özelliğini olarak ayarlamanız gerekir `true` . Aksi takdirde, yerelleştirilmiş yükleme metni yok sayılır.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>VSIX özelliğinde Içerme özelliğini ayarlamak için  
  
1. **Çözüm Gezgini**, Extension. valtlangpack dosyasına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. Özellik kılavuzunda **VSIX 'e Ekle**' ye tıklayın ve değerini olarak ayarlayın `true` .  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek, bir Extension. valtmanifest dosyasının ilgili bölümlerini, Ispanyolca için karşılık gelen uzantı. valtlangpack dosyası ile birlikte gösterir. Dil paketindeki değerler, hedef bilgisayarın Visual Studio yerel ayarı Ispanyolca olarak ayarlandıysa, bildirim içindeki değerleri değiştirin.  
  
### <a name="code"></a>Kod  
 [Extension. valtmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension. valtlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSıX LanguagePack öğesi](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [VSıX paketinin anatomumu](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX Proje Şablonu](../extensibility/vsix-project-template.md)
