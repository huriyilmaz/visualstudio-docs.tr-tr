---
title: Dizeleri Öğe | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699728"
---
# <a name="strings-element"></a>Strings Öğesi
Strings öğesi en az bir **ButtonText** alt öğesi içermelidir. Diğer tüm alt öğeler isteğe bağlıdır. '&' ve '<' gibi geçersiz XML karakterleri varlıklar ('&amp;ve '&lt;' ve ' ' ' vb.) olarak kodlanmalıdır.

 Metin dizesinde bir ampersand komutu için klavye kısayolu belirtir.

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
|language|İsteğe bağlı. Dil=".".|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|Düğme Metni|Bu alan ve komut tanımında aşağıdaki beş metin alanı, çeşitli menülerde görünen metni belirtmenize izin verir. Varsayılan olarak, `ButtonText` alan menü denetleyicilerinde görünür. Diğer `ButtonText` metin alanları boşsa alan da varsayılan olur. Diğer `ButtonText` metin alanları belirtilse bile alan boş olamaz.|
|Tooltiptext|Alan, `ToolTipText` bir menü öğesinin araç ucunda görünen metni belirtir.<br /><br /> `ToolTipText` Alan boşsa, `ButtonText` alan kullanılır.|
|Menü Metni|Alan, `MenuText` ana menüde, araç çubuğunda, kısayol menüsünde veya alt menüde yse komut için görüntülenen metni belirtir. `MenuText` Alan boşsa, `ButtonText` tümleşik geliştirme ortamı (IDE) alanı kullanır. Alan `MenuText` yerelleştirme için de kullanılabilir.<br /><br /> Kısayol menüleri için `MenuText` alan, Kısayol Menüleri araç çubuğunda görüntülenen ve IDE'deki kısayol menülerinin özelleştirilmesini sağlayan addır. Bu nedenle, kısayol menünüzü niçin adlandırdığınızkonusunda açık olun; örneğin, "Kısayol" yerine "Widget Paketi Kısayol Menüsü"nü kullanın.<br /><br /> `MenuText` Alan belirtilmemişse, `ButtonText` alan kullanılır.|
|Commandname|Alan, `CommandName` **Özelleştir** iletişim kutusundaki **Komutlar** sekmesinde klavye kategorisinde görünen metni belirtir **(Araçlar** menüsünde **Özelleştir'i** tıklatarak kullanılabilir).|
|CanonicalName|İngilizce `CanonicalName` alan, menü öğesini yürütmek için **Komut** penceresinde girilebilen İngilizce metinde komutun adını belirtir. IDE, harf, basamak, alt çizineç veya katıştırılmış dönemler olmayan karakterleri şeritler. Bu metin daha sonra komutu `ButtonText` tanımlamak için alana kısıtlanır. Örneğin, **Dosya** menüsündeki **Yeni Proje,** File.NewProject komutu olur.<br /><br /> İngilizce `CanonicalName` alan belirtilmemişse, IDE `ButtonText` alanı kullanır ve harfler, basamaklar, alt çizerler ve gömülü dönemler hariç tüm dönemleri şeritler. Örneğin, Düğme Metni "komutları &tanımla..." ampersand, boşluk ve elips kaldırılır DefineKomutları olur.<br /><br /> `TextChanges` Bayrak belirtilir ve komutun metni değiştirilirse, **Komut** penceresi tarafından tanınan ilgili komut değişmez; orijinal `ButtonText` veya İngilizce `CanonicalName` alanların kanonik formu olmaya devam eder.|
|LocCanonicalName|Alan, `LocCanonicalName` İngilizce `CanonicalName` alanına aynı şekilde çalışır, ancak yerelleştirilmiş komut metninin belirtilmesini sağlar. Her iki kanonik alan belirtilebilir. IDE **komut** penceresinde girilen metni ayrıştAmave bir komutla ilişkilendirdiği için, hem İngilizce hem de İngilizce olmayan metin aynı komutla ilişkilendirilebilir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Button Öğesi](../extensibility/button-element.md)|Kullanıcının etkileşimkurabileceği bir öğe tanımlar.|
|[Menu Öğesi](../extensibility/menu-element.md)|Tek bir menü öğesi tanımlar.|
|[Combo Öğesi](../extensibility/combo-element.md)|Açılan kutuda görünen komutları tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
