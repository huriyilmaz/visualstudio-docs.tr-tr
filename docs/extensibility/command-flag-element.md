---
title: Komut bayrağı öğesi | Microsoft Docs
description: Komut bayrağı öğesi, üst öğesini değiştirir. Üst öğelerini ve alt öğelerini gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6356fd02c8045aee9dc48ebc9d30a346159080bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902039"
---
# <a name="command-flag-eelement"></a>Komut bayrağı Eelement
Üst öğesini değiştirir.

## <a name="syntax"></a>Syntax

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümde geçerli öğe değerleri açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Değer|Açıklama|
|-----------|-----------------|
|AllowParams|Kullanıcıların, komutun kurallı adını yazdıklarında **komut penceresinde komut** parametreleri girebilecekleri anlamına gelir.<br /><br /> Geçerli: `Button`|
|AlwaysCreate|Menü, Grup veya düğme içermediğinden bile oluşturulur.<br /><br /> Geçerli: `Menu`|
|CaseSensitive|Kullanıcı girdileri büyük/küçük harfe duyarlıdır.<br /><br /> Geçerli: `Combo`|
|Yalnızca commandwell|Bu bayrağı, komut üst düzey menüde görünmezse ve örneğin bir klavye kısayoluna bağlamak için ek kabuk özelleştirmesi için kullanılabilir hale getirmek istiyorsanız uygulayın. VSPackage yüklendikten sonra, **Seçenekler** iletişim kutusunu açıp sonra **klavye ortamı** kategorisi altındaki komut yerleşimini düzenleyerek bu komutları özelleştirebilirsiniz. Bu bayrak, kısayol menülerinde, araç çubuklarında, menü denetleyicilerinde veya alt menülerde yerleşimi etkilemez.<br /><br /> Geçerli: `Button` , `Combo`|
|DefaultDisabled|Varsayılan olarak, uygulayan VSPackage yüklü değilse veya `QueryStatus` Yöntem çağrılmışsa komut devre dışıdır.<br /><br /> Geçerli: `Button` , `Combo`|
|Defaultsabitlenmiş|Varsayılan olarak yerleştirildi. Bu ayar her zaman yerleştirilmiş olduklarından araç çubukları için geçerli değildir.|
|Defaulınvisible|Varsayılan olarak, uygulayan VSPackage yüklü değilse veya `QueryStatus` Yöntem çağrılmışsa, komut görünmez.<br /><br /> Bunu bayrağıyla birleştirmeniz önerilir `DynamicVisibility` .<br /><br /> Geçerli: `Button` , `Combo` , `Menu`|
|DontCache|Geliştirme ortamı, `QueryStatus` Bu komut için yöntem sonuçlarını önbelleğe almaz.<br /><br /> Bir menü için bu, menü denetleyicisinin menü öğelerinin metnini önbelleğe yazmayacağını söyler. Menü dinamik öğeleri veya dinamik metin içeren öğeleri içerdiğinde bu bayrağı kullanın.<br /><br /> Geçerli: `Button` , `Menu`|
|DynamicItemStart|Dinamik bir listenin başlangıcını gösterir. Bu, `QueryStatus` OLECMDERR_E_UNSUPPORTED bayrağı döndürülünceye kadar, ortamı liste öğeleri üzerinde sırayla çağırarak, ortamın bir liste oluşturmasını sağlar. Bu, en son kullanılanlar (MRU) listeleri ve pencere listeleri gibi öğeler için iyi bir sonuç verir.<br /><br /> Geçerli: `Button`|
|DynamicVisibility|Komutun görünürlüğü, `QueryStatus` yöntemi aracılığıyla veya bölümüne eklenen bir bağlam GUID 'si aracılığıyla değiştirilebilir `VisibilityConstraints` .<br /><br /> Menülerde ve araç penceresi araç çubuklarında görüntülenen komutlar için geçerlidir, ancak ana pencerede görünen en üst düzey araç çubuklarında değildir. Yönteminden OLECMDF_INVISIBLE bayrağı döndürüldüğünde, üst düzey araç çubuğu öğeleri devre dışı bırakılabilir ancak gizlenemez `QueryStatus` . Araç penceresi araç çubuklarında görünen araç çubuğu komutları gizlenebilir.<br /><br /> Bir menüde, bu bayrak, tüm üyeleri gizli olduğunda otomatik olarak gizlenmesi gerektiğini de belirtir. Üst düzey menülerde bu davranış zaten olduğu için bu bayrak genellikle alt menülere atanır.<br /><br /> Bu bayrak bayrağıyla birleştirilmelidir `DefaultInvisible` .<br /><br /> Geçerli: `Button` , `Combo` , `Menu`|
|'Nı|[Birleşik giriş öğesi](../extensibility/combo-element.md)altındaki filtreleme anahtarları konusuna bakın.<br /><br /> Geçerli: `Combo`|
|FixMenuController|Bu komut bir menü denetleyicisine yerleştirilse, komut her zaman varsayılandır; diğer bir deyişle, menü denetleyicisi düğmesi her seçildiğinde komut seçilir. Menü denetleyicisi `TextIsAnchorCommand` bayrak ayarlandıysa, menü denetleyicisi de onun metnini, bayrağını içeren komuttan alır `FixMenuController` .<br /><br /> Bir menü denetleyicisindeki yalnızca bir komutun `FixMenuController` bayrağı olmalıdır. Birden fazla komut işaretlenmişse, menüdeki son komut varsayılan komut olur.<br /><br /> Geçerli: `Button`|
|IconAndText|Menü ve araç çubuğunda simge ve metin gösterme.<br /><br /> Geçerli: `Button` , `Combo` , `Menu`|
|NoAutoComplete|Otomatik tamamlanma özelliği devre dışı.<br /><br /> Geçerli: `Combo`|
|NoButtonCustomize|Kullanıcının bu düğmeyi özelleştirmesine izin vermeyin.<br /><br /> Geçerli: `Button` , `Combo`|
|NoKeyCustomize|Klavye özelleştirmesini etkinleştirmeyin.<br /><br /> Geçerli: `Button` , `Combo`|
|NoShowOnMenuController|Bu komut bir menü denetleyicisinde konumlandırılmışsa, komut açılan listede görünmez.<br /><br /> Geçerli: `Button`|
|NotInTBList|Kullanılabilir araç çubukları listesinde görünmez. Bu yalnızca araç çubuğu menü türleri için geçerlidir.<br /><br /> Geçerli: `Menu`|
|NoToolbarClose|Kullanıcı araç çubuğunu kapatamıyor. Bu yalnızca araç çubuğu menü türleri için geçerlidir.<br /><br /> Geçerli: `Menu`|
|Resim|Yalnızca bir araç çubuğunda simge göster, ancak menüdeki metin. Hiçbir simge belirtilmemişse, bir araç çubuğunda tıklatılabilir boş bir boşluk gösterir.<br /><br /> Geçerli: `Button`|
|PostExec|Komutu engellenmemiş hale getirir. Geliştirme ortamı, tüm ön işleme sorguları tamamlanana kadar yürütmeyi erteler.<br /><br /> Geçerli: `Button`|
|RouteToDocs|Komut etkin belgeye yönlendirilir.<br /><br /> Geçerli: `Button`|
|Yatay olarak|Bu bayrak ayar olduğunda genişlik, birleşik giriş kutusu için en düşük genişlik haline gelir ve araç çubuğunda yer varsa birleşik giriş kutusu kullanılabilir alanı dolduracak şekilde esnetilebilir. Bu yalnızca araç çubuğu yatay olarak yerleştirildi ve araç çubuğundaki yalnızca bir birleşik giriş kutusu bayrağını kullanabilirse (bayrak ilk birleşik giriş kutusu dışında hepsinde yoksayılır) oluşur.<br /><br /> Şu için geçerlidir: `Combo`|
|TextChanges|Komut veya menü metni, genellikle yöntemi aracılığıyla çalışma zamanında `QueryStatus` değiştirilebilir.<br /><br /> Şu için geçerlidir: `Button` , `Menu`|
|TextChangesButton|Şu için geçerlidir: `Button`|
|TextIsAnchorCommand|Menü denetleyicisi için, menenin metni varsayılan (sabit noktası) komutundan alınır. Sabit noktası komutu, seçilen veya kilitli son komut. Bu bayrak ayarlanmazsa menü denetleyicisi kendi alanını `MenuText` kullanır. Ancak, menü denetleyicisine tıklarken ilgili denetleyiciden son seçilen komut yine de kullanılabilir.<br /><br /> Bu bayrağı bayrağıyla birleştirmenizi `TextChanges` öneririz.<br /><br /> Bu bayrak yalnızca MenuController veya MenuControllerLatched türünde menüler için geçerlidir.<br /><br /> Şu için geçerlidir: `Menu`|
|TextMenuCtrlUseMenu|Menü `MenuText` denetleyicilerinde alanını kullanın. Varsayılan alan' `ButtonText` dır.<br /><br /> Şu için geçerlidir: `Button`|
|TextMenuUseButton|Menüler `ButtonText` için alanını kullanın. Varsayılan alan, `MenuText` belirtilmişse değeridir.<br /><br /> Şu için geçerlidir: `Button`|
|Textonly|Bir araç çubuğunda veya menüde yalnızca metin gösterir, ancak simge belirtilmiş olsa bile simge göstermez.<br /><br /> Şu için geçerlidir: `Button`|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Düğme öğesi öğeleri için [bir grup](../extensibility/button-element.md) sağlar.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uygulayan tüm menüleri tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu () seçin. Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
