---
title: Dizeler öğesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719439"
---
# <a name="strings-element"></a>Strings Öğesi
Dizeler öğesi en az bir **ButtonText** alt öğesi içermelidir. Diğer tüm alt öğeler isteğe bağlıdır. ' & ' Ve ' < ' gibi geçersiz XML karakterleri, varlıklar (' &amp; ' ve ' &lt; ' vb.) olarak kodlanmalıdır.

 Metin dizesindeki bir ve işareti, komutun klavye kısayolunu belirtir.

## <a name="syntax"></a>Sözdizimi

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|dil|İsteğe bağlı. Dil = ".".|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|ButtonText|Bu alan ve bir komut tanımındaki aşağıdaki beş metin alanı, çeşitli menülerde görüntülenen metni belirtmenize izin verir. Varsayılan olarak, `ButtonText` alanı menü denetleyicileri ' nde görünür. Diğer metin alanları boşsa, `ButtonText` alanı da varsayılan olur. Diğer metin alanları belirtiseler bile `ButtonText` alanı boş bırakılamaz.|
|TOOLTIPTEXT|@No__t_0 alanı, bir menü öğesi için araç ipucunda görüntülenen metni belirtir.<br /><br /> @No__t_0 alanı boşsa, `ButtonText` alanı kullanılır.|
|MenuText|@No__t_0 alanı, ana menü, araç çubuğu, kısayol menüsü veya alt menüdeki bir komut için görüntülenen metni belirtir. @No__t_0 alanı boşsa, tümleşik geliştirme ortamı (IDE) `ButtonText` alanını kullanır. @No__t_0 alanı yerelleştirme için de kullanılabilir.<br /><br /> Kısayol menüleri için `MenuText` alanı, IDE 'de kısayol menülerinin özelleştirilmesine izin veren kısayol menüleri araç çubuğunda görüntülenen addır. Bu nedenle, kısayol menünüzün adına özel olun; Örneğin, "kısayol" yerine "pencere öğesi paketi kısayol menüsü" kullanın.<br /><br /> @No__t_0 alanı belirtilmemişse, `ButtonText` alanı kullanılır.|
|Name|@No__t_0 alanı, **Özelleştir** Iletişim kutusundaki **Komutlar** sekmesinde bulunan klavye kategorisinde görüntülenen metni belirtir ( **Araçlar** menüsünde **Özelleştir** ' i tıklatarak kullanılabilir).|
|CanonicalName|Ingilizce `CanonicalName` alanı, menü öğesini yürütmek için **komut** penceresine girilebilecek İngilizce metinde komutun adını belirtir. IDE, harf, rakam, alt çizgi veya gömülü nokta olmayan karakterleri kaldırır. Bu metin daha sonra komutu tanımlamak için `ButtonText` alanına birleştirilir. Örneğin, **Dosya** menüsündeki **Yeni proje** File. NewProject komutu olur.<br /><br /> Ingilizce `CanonicalName` alanı belirtilmemişse, IDE `ButtonText` alanını kullanır ve harfler, rakamlar, alt çizgiler ve gömülü dönemler hariç tümünü kaldırır. Örneğin, düğme metni "& komutları tanımla..." , ve işareti, boşluk ve üç noktanın kaldırıldığı DefineCommands olur.<br /><br /> @No__t_0 bayrağı belirtilirse ve komutun metni değiştirilirse, **komut** penceresi tarafından tanınan karşılık gelen komut değişmez; özgün `ButtonText` veya Ingilizce `CanonicalName` alanlarının kurallı biçimi kalır.|
|LocCanonicalName|@No__t_0 alanı Ingilizce `CanonicalName` alanla aynı şekilde davranır, ancak yerelleştirilmiş komut metninin belirtilmesini sağlar. Her iki kurallı alan de belirtilebilir. IDE, **komut** penceresinde girilen metni ayrıştırır ve bunu bir komutla ilişkilendirir, hem İngilizce hem de İngilizce olmayan metinler aynı komutla ilişkilendirilebilir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Button Öğesi](../extensibility/button-element.md)|Kullanıcının etkileşime girebileceği bir öğe tanımlar.|
|[Menu Öğesi](../extensibility/menu-element.md)|Tek bir menü öğesi tanımlar.|
|[Combos Öğesi](../extensibility/combo-element.md)|Birleşik giriş kutusunda görünen komutları tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)