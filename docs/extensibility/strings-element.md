---
title: Strings Öğesi | Microsoft Docs
description: Strings öğesi bir ButtonText alt öğesi ve diğer isteğe bağlı alt öğeleri içerir. Metin dizesinde ve karakteri bir klavye kısayolu belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899413"
---
# <a name="strings-element"></a>Strings Öğesi
Strings öğesi en az bir **ButtonText alt** öğesi içermeli. Diğer tüm alt öğeler isteğe bağlıdır. '&' ve '<' gibi geçersiz XML karakterleri varlık (' ' &amp; ve ' &lt; ' gibi) olarak kodlamalıdır.

 Metin dizesinde ve karakteri, komutun klavye kısayolunu belirtir.

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
|language|İsteğe bağlı. Language=".".|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|ButtonText|Bu alan ve komut tanımında aşağıdaki beş metin alanı, çeşitli menülerde görüntülenen metni belirtmenize izin verir. Varsayılan olarak, alan `ButtonText` menü denetleyicilerinde görünür. Diğer `ButtonText` metin alanları boşsa alan da varsayılan olur. Diğer `ButtonText` metin alanları belirtilmiş olsa bile alan boş olamaz.|
|Tooltiptext|`ToolTipText`alanı, bir menü öğesinin araç ipucunda görünen metni belirtir.<br /><br /> Alan `ToolTipText` boşsa alanı `ButtonText` kullanılır.|
|MenuText|alanı, ana menüde, araç çubuğunda, kısayol menüsünde veya bir alt menüde yer alan komut için `MenuText` görüntülenen metni belirtir. Alan `MenuText` boşsa tümleşik geliştirme ortamı (IDE) alanını `ButtonText` kullanır. Alanı `MenuText` yerelleştirme için de kullanılabilir.<br /><br /> Kısayol menüleri için, alanı Kısayol Menüleri araç çubuğunda görüntülenen addır ve bu ad IDE'de kısayol menülerinin `MenuText` özelleştirilmesini sağlar. Bu nedenle, kısayol menüyü nasıl adla ifade ettiyebilirsiniz; Örneğin, "Kısayol" yerine "Pencere Öğesi Paketi Kısayol Menüsü" kullanın.<br /><br /> Alan `MenuText` belirtilmezse, `ButtonText` alanı kullanılır.|
|Commandname|alanı, Özelleştir iletişim kutusundaki Komutlar sekmesindeki klavye kategorisinde görüntülenen metni belirtir (Araçlar menüsünde `CommandName` **Özelleştir'e** tıklayarak **kullanılabilir).**  |
|CanonicalName|İngilizce alanı, menü öğesini yürütmek için Komut penceresine girilebilir İngilizce `CanonicalName` **metinde** komutun adını belirtir. IDE harf, basamak, alt çizgi veya eklenmiş nokta değil tüm karakterleri çıkartır. Bu metin daha sonra komutu tanımlamak `ButtonText` için alanıyla birtir. Örneğin, **Dosya menüsündeki** Yeni **Proje,** File.NewProject komutu olur.<br /><br /> İngilizce alanı belirtilmezse, IDE alanını kullanır ve harf, basamak, alt çizgi ve eklenmiş nokta dışındaki `CanonicalName` `ButtonText` tüm alanları çıkartır. Örneğin, Düğme Metni "&Tanımla..." ve ve, boşluk ve üç noktanın kaldırıldığı DefineCommands olur.<br /><br /> Bayrak belirtilirse ve komutun metni değiştirilirse, Komut penceresi tarafından tanınan karşılık gelen komut değişmez; özgün veya İngilizce alanların kurallı `TextChanges`  `ButtonText` biçimi `CanonicalName` kalır.|
|LocCanonicalName|alanı `LocCanonicalName` İngilizce alanıyla aynı şekilde `CanonicalName` davranır, ancak yerelleştirilmiş komut metninin belirtilebilir. Her iki kurallı alan da belirtilebilir. IDE Yalnızca Komut penceresine girilen  metni ayrıştırarak bir komutla ilişkilendirene kadar, hem İngilizce hem de İngilizce olmayan metinler aynı komutla ilişkilendirilebilirsiniz.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Button Öğesi](../extensibility/button-element.md)|Kullanıcının etkileşimde buluna bir öğeyi tanımlar.|
|[Menu Öğesi](../extensibility/menu-element.md)|Tek bir menü öğesini tanımlar.|
|[Combo Öğesi](../extensibility/combo-element.md)|Birleşik giriş kutusunda görünen komutları tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
