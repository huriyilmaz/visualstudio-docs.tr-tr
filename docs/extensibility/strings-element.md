---
title: Dizeler öğesi | Microsoft Docs
description: Dizeler öğesi bir ButtonText alt öğesi ve diğer isteğe bağlı alt öğeleri içerir. Metin dizesindeki bir ve işareti klavye kısayolunu belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7951d0c72c3fd6a1897224d9606abdfec9a60053
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848018"
---
# <a name="strings-element"></a>Strings Öğesi
Dizeler öğesi en az bir **ButtonText** alt öğesi içermelidir. Diğer tüm alt öğeler isteğe bağlıdır. ' & ' ve ' < ' gibi geçersiz XML karakterleri, varlıklar (' &amp; ' ve ' ' vb.) olarak kodlanmalıdır &lt; .

 Metin dizesindeki bir ve işareti, komutun klavye kısayolunu belirtir.

## <a name="syntax"></a>Syntax

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
|language|İsteğe bağlı. Dil = ".".|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|ButtonText|Bu alan ve bir komut tanımındaki aşağıdaki beş metin alanı, çeşitli menülerde görüntülenen metni belirtmenize izin verir. Varsayılan olarak, `ButtonText` alan menü denetleyicileri ' nde görünür. `ButtonText`Diğer metin alanları boşsa, alan de varsayılan olur. `ButtonText`Diğer metin alanları belirtiseler bile alanı boş bırakılamaz.|
|TOOLTIPTEXT|`ToolTipText`Alan, bir menü öğesi için araç ipucunda görüntülenen metni belirtir.<br /><br /> `ToolTipText`Alan boşsa, `ButtonText` alanı kullanılır.|
|MenuText|`MenuText`Bu alan, ana menü, araç çubuğu, kısayol menüsü veya alt menüdeki bir komut için görüntülenen metni belirtir. `MenuText`Alan boşsa, tümleşik geliştirme ortamı (IDE) `ButtonText` alanını kullanır. `MenuText`Alan, yerelleştirme için de kullanılabilir.<br /><br /> Kısayol menüleri için, `MenuText` Bu alan kısayol menüleri araç çubuğunda görüntülenen, IDE 'de kısayol menülerinin özelleştirilmesine izin veren addır. Bu nedenle, kısayol menünüzün adına özel olun; Örneğin, "kısayol" yerine "pencere öğesi paketi kısayol menüsü" kullanın.<br /><br /> `MenuText`Alan belirtilmemişse, `ButtonText` alanı kullanılır.|
|Name|`CommandName`Alan, **Özelleştir** iletişim kutusundaki **Komutlar** sekmesinde klavye kategorisinde görüntülenen metni belirtir ( **Araçlar** menüsünde **Özelleştir** ' i tıklatarak kullanılabilir).|
|CanonicalName|Ingilizce `CanonicalName` alanı, menü öğesini yürütmek Için **komut** penceresine girilebilecek İngilizce metindeki komutun adını belirtir. IDE, harf, rakam, alt çizgi veya gömülü nokta olmayan karakterleri kaldırır. Bu metin daha sonra `ButtonText` komutu tanımlamak için alana birleştirilir. Örneğin, **Dosya** menüsündeki **Yeni proje** File. NewProject komutu olur.<br /><br /> Ingilizce `CanonicalName` alanı belirtilmemişse, IDE `ButtonText` alanı kullanır ve harfler, rakamlar, alt çizgiler ve gömülü dönemler hariç tümünü kaldırır. Örneğin, düğme metni "&komutları tanımla..." , ve işareti, boşluk ve üç noktanın kaldırıldığı DefineCommands olur.<br /><br /> `TextChanges`Bayrak belirtilmişse ve komutun metni değiştirilirse, **komut** penceresi tarafından tanınan karşılık gelen komut değişmez; orijinal `ButtonText` veya İngilizce alanlarının kurallı biçimi kalır `CanonicalName` .|
|LocCanonicalName|`LocCanonicalName`Alan, İngilizce alanla aynı şekilde davranır, `CanonicalName` ancak yerelleştirilmiş komut metninin belirtilmesini sağlar. Her iki kurallı alan de belirtilebilir. IDE, **komut** penceresinde girilen metni ayrıştırır ve bunu bir komutla ilişkilendirir, hem İngilizce hem de İngilizce olmayan metinler aynı komutla ilişkilendirilebilir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Button Öğesi](../extensibility/button-element.md)|Kullanıcının etkileşime girebileceği bir öğe tanımlar.|
|[Menu Öğesi](../extensibility/menu-element.md)|Tek bir menü öğesi tanımlar.|
|[Combo Öğesi](../extensibility/combo-element.md)|Birleşik giriş kutusunda görünen komutları tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
