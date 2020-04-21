---
title: Komut Bayrak Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649362"
---
# <a name="command-flag-eelement"></a>Komut bayrağı Eelement
Ana öğesini değiştirir.

## <a name="syntax"></a>Sözdizimi

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
|İzin Params|Kullanıcıların **komutun** kanonik adını yazarken Komut penceresine komut parametrelerini girebileceğini belirtir.<br /><br /> Geçerli:`Button`|
|Her Zaman Oluştur|Menü, grubu veya düğmesi olmasa bile oluşturulur.<br /><br /> Geçerli:`Menu`|
|Casesensitive|Kullanıcı girişleri büyük/küçük harf duyarlıdır.<br /><br /> Geçerli:`Combo`|
|CommandwellOnly|Komut üst düzey menüde görünmüyorsa ve örneğin klavye kısayoluna bağlamak için ek kabuk özelleştirmesi için kullanılabilir hale getirmek istiyorsanız bu bayrağı uygulayın. VSPackage yüklendikten sonra, **Seçenekler** iletişim kutusunu açıp **klavye ortamı** kategorisi altında komut yerleşimini düzenleyerek bu komutları özelleştirebilirsiniz. Bu bayrak, kısayol menülerinde, araç çubuklarına, menü denetleyicilerine veya alt menülere yapılan yerleşimi etkilemez.<br /><br /> Geçerli: `Button`,`Combo`|
|Varsayılan Devre|Varsayılan olarak, bunu uygulayan VSPackage yüklenmezse veya `QueryStatus` yöntem çağrılmazsa komut devre dışı bırakılır.<br /><br /> Geçerli: `Button`,`Combo`|
|Varsayılan Docked|Varsayılan olarak sabitlenmiştir. Bu ayar, her zaman sabitlendikleri için artık araç çubukları için geçerli değildir.|
|Varsayılan Görünmez|Varsayılan olarak, bunu uygulayan VSPackage yüklenmezse veya `QueryStatus` yöntem çağrılmazsa komut görünmezdir.<br /><br /> Bunu bayrakla birleştirmenizi `DynamicVisibility` öneririz.<br /><br /> Geçerli: `Button`, `Combo`,`Menu`|
|DontÖnbellek|Geliştirme ortamı, bu komut `QueryStatus` için yöntem sonuçlarını önbelleğe almaz.<br /><br /> Bir menü için bu, menü öğelerinin metnini önbelleğe almayan bir menü denetleyicisine söyler. Menü dinamik öğeler veya dinamik metin içeren öğeler içeriyorsa bu bayrağı kullanın.<br /><br /> Geçerli: `Button`,`Menu`|
|DynamicItemStart|Dinamik bir listenin başlangıcını gösterir. Bu, OLECMDERR_E_UNSUPPORTED bayrağı döndürülene kadar liste `QueryStatus` öğelerindeki yöntemi art arda çağırarak ortamın bir liste oluşturmasını sağlar. Bu, en son kullanılan (MRU) listeleri ve pencere listeleri gibi öğeler için iyi çalışır.<br /><br /> Geçerli:`Button`|
|DinamikGörünürlük|Komutun görünürlüğü `QueryStatus` yöntem veya `VisibilityConstraints` bölüme dahil olan bir bağlam GUID ile değiştirilebilir.<br /><br /> Menülerde ve araç penceresi araç çubuklarında görünen, ancak ana pencerede görünen üst düzey araç çubuklarında görünmeyen komutlar için geçerlidir. Üst düzey araç çubuğu öğeleri, OLECMDF_INVISIBLE bayrağı `QueryStatus` yöntemden döndürüldüğünde devre dışı bırakılmış, ancak gizli tutulamaz. Araç penceresi araç çubuklarında görünen araç çubuğu komutları gizlenebilir.<br /><br /> Menüde, bu bayrak, tüm üyeleri gizlendiğinde otomatik olarak gizlenmesi gerektiğini de belirtir. Üst düzey menülerde zaten bu davranış olduğundan, bu bayrak genellikle alt menülere atanır.<br /><br /> Bu bayrak `DefaultInvisible` bayrakla birleştirilmelidir.<br /><br /> Geçerli: `Button`, `Combo`,`Menu`|
|Filtre Tuşları|[Combo Elementi](../extensibility/combo-element.md)altındaki Filtreleme Anahtarları konusuna bakın.<br /><br /> Geçerli:`Combo`|
|FixMenuController|Bu komut bir menü denetleyicisi üzerinde konumlandırılmışsa, komut her zaman varsayılandır; diğer bir de menü denetleyici düğmesinin kendisi seçildiğinde komut seçilir. Menü denetleyicisi `TextIsAnchorCommand` bayrak kümesine sahipse, menü denetleyicisi de `FixMenuController` metnini bayrak olan komuttan alır.<br /><br /> Bir menü denetleyicisi üzerinde `FixMenuController` yalnızca bir komut bayrak olmalıdır. Birden fazla komut bu kadar işaretlenmişse, menüdeki son komut varsayılan komut olur.<br /><br /> Geçerli:`Button`|
|Simgeve Metin|Menü de ve araç çubuğunda bir simge ve metin gösterin.<br /><br /> Geçerli: `Button`, `Combo`,`Menu`|
|NoAutoComplete|Otomatik tamamlama özelliği devre dışı bırakılır.<br /><br /> Geçerli:`Combo`|
|NoButtonCustomizE|Kullanıcının bu düğmeyi özelleştirmesine izin vermeyin.<br /><br /> Geçerli: `Button`,`Combo`|
|NoKeyCustomizE|Klavye özelleştirmeyi etkinleştirme.<br /><br /> Geçerli: `Button`,`Combo`|
|NoShowonMenuController|Bu komut bir menü denetleyicisi üzerinde konumlandırılmışsa, komut açılır listede görünmez.<br /><br /> Geçerli:`Button`|
|Notintblist|Kullanılabilir araç çubukları listesinde görünmüyor. Bu yalnızca Araç Çubuğu menü türleri için geçerlidir.<br /><br /> Geçerli:`Menu`|
|NoToolbarClose|Kullanıcı araç çubuğunu kapatamaz. Bu yalnızca Araç Çubuğu menü türleri için geçerlidir.<br /><br /> Geçerli:`Menu`|
|Pıct|Araç çubuğunda yalnızca bir simge, ancak menüde yalnızca metin gösterin. Simge belirtilmemişse, araç çubuğunda tıklanabilir boş alan gösterir.<br /><br /> Geçerli:`Button`|
|PostExec|Komutu engellemeyen yapar. Geliştirme ortamı, tüm ön işleme sorguları tamamlanana kadar yürütmeyi erteler.<br /><br /> Geçerli:`Button`|
|RouteToDocs|Komut etkin belgeye yönlendirilir.<br /><br /> Geçerli:`Button`|
|StretchYatay|Bu bayrak ayarlandığında, genişlik açılan kutu için minimum genişlik olur ve araç çubuğunda yer varsa, açılan kutu kullanılabilir alanı doldurmak için uzanır. Bu yalnızca araç çubuğu yatay olarak sabitlenmişse ve araç çubuğundaki yalnızca bir açılan kutu bayrağı kullanabilirse (bayrak ilk açılan kutu dışında tüm bunlara göz ardı edilir).<br /><br /> Geçerli:`Combo`|
|Metin Değişiklikleri|Komut veya menü metni genellikle `QueryStatus` yöntem aracılığıyla çalışma zamanında değiştirilebilir.<br /><br /> Geçerli: `Button`,`Menu`|
|Metin DeğişiklikleriDüğme|Geçerli:`Button`|
|TextisAnchorCommand|Menü denetleyicisi için, menünün metni varsayılan (çapa) komutundan alınır. Çapa komutu seçilen veya kilitlenen son komutdur. Bu bayrak ayarlı değilse, menü denetleyicisi kendi `MenuText` alanını kullanır. Ancak, menü denetleyicisini tıklattığınızda yine de bu denetleyiciden seçilen son komutu etkinleştirin.<br /><br /> Bu bayrağı `TextChanges` bayrakla birleştirmenizi öneririz.<br /><br /> Bu bayrak yalnızca MenuController veya MenuControllerLatched türü menüler için geçerlidir.<br /><br /> Geçerli:`Menu`|
|TextMenuCtrlUseMenu|Menü `MenuText` denetleyicileri üzerinde alanı kullanın. Varsayılan alan `ButtonText`.<br /><br /> Geçerli:`Button`|
|TextMenuUseButton|Menüler `ButtonText` için alanı kullanın. Varsayılan alan `MenuText` belirtilirse.<br /><br /> Geçerli:`Button`|
|Textonly|Yalnızca bir araç çubuğunda veya menüde metin gösterin, ancak simge belirtilmiş olsa bile simge yi göstermeyin.<br /><br /> Geçerli:`Button`|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|[Düğme öğesi](../extensibility/button-element.md) öğeleri için bir grup sağlar.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uyguladığı tüm menüleri tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
