---
title: Komut bayrağı öğesi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649362"
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
|Yatay olarak|Bu bayrak ayarlandığında, Genişlik Birleşik giriş kutusunun en düşük genişliği olur ve araç çubuğunda yer varsa, Birleşik giriş kutusu kullanılabilir alanı dolduracak şekilde uzatılır. Bu yalnızca araç çubuğu yatay olarak yuvalanmışsa ve araç çubuğunda yalnızca bir açılan kutu bayrağını kullanıyorsa oluşur (bayrak ilk Birleşik giriş kutusu hariç tüm üzerinde yok sayılır).<br /><br /> Geçerli: `Combo`|
|TextChanges|Komut veya menü metni, genellikle yöntemi aracılığıyla çalışma zamanında değiştirilebilir `QueryStatus` .<br /><br /> Geçerli: `Button` , `Menu`|
|TextChangesButton|Geçerli: `Button`|
|TextIsAnchorCommand|Bir menü denetleyicisi için, menünün metni varsayılan (tutturucu) komutundan alınır. Bir tutturucu komutu seçili veya eksik olan son komuttur. Bu bayrak ayarlanmamışsa, menü denetleyicisi kendi `MenuText` alanını kullanır. Ancak, menü denetleyicisine tıkladığınızda bu denetleyicideki son seçili komut hala etkinleştirilir.<br /><br /> Bu bayrağı bayrağıyla birleştirmeniz önerilir `TextChanges` .<br /><br /> Bu bayrak yalnızca MenuController veya Menucontrollerlalenmiş menüler için geçerlidir.<br /><br /> Geçerli: `Menu`|
|TextMenuCtrlUseMenu|`MenuText`Menü denetleyicileri üzerinde alanını kullanın. Varsayılan alan `ButtonText` .<br /><br /> Geçerli: `Button`|
|TextMenuUseButton|`ButtonText`Menüler için alanını kullanın. Varsayılan alan `MenuText` belirtilmişse.<br /><br /> Geçerli: `Button`|
|TextOnly|Yalnızca bir araç çubuğunda veya menüde metin göster, ancak simge belirtilmiş olsa bile simge yok.<br /><br /> Geçerli: `Button`|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|[Düğme öğesi](../extensibility/button-element.md) öğeleri için bir grup sağlar.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage 'ın uyguladığı tüm menüleri tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
