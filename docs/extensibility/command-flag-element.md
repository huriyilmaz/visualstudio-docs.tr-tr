---
title: Komut Bayrağı Öğesi | Microsoft Docs
description: Komut bayrağı Öğesi, üst öğesini değiştiren öğedir. Üst öğelerini ve alt öğelerini gözden geçirme.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1be87038e7baedaac0ea1244b8acfc500c70a2c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111976"
---
# <a name="command-flag-eelement"></a>Komut bayrağı Eelement
Üst öğesinin değişikliklerini sağlar.

## <a name="syntax"></a>Syntax

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümde geçerli öğe değerleri açık almaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Değer|Açıklama|
|-----------|-----------------|
|AllowParams|Kullanıcıların komutun kurallı adını **yazarak Komut** penceresine komut parametreleri girebilirsiniz.<br /><br /> Şu için geçerlidir: `Button`|
|AlwaysCreate|Menü, grup veya düğme yoksa bile oluşturulur.<br /><br /> Şu için geçerlidir: `Menu`|
|Casesensitive|Kullanıcı girişleri büyük/büyük/büyük harfe duyarlıdır.<br /><br /> Şu için geçerlidir: `Combo`|
|CommandWellOnly|Komut üst düzey menüde görünmüyorsa ve ek kabuk özelleştirmesi için kullanılabilir hale (örneğin, bir klavye kısayolu bağlama gibi) bu bayrağı uygulayabilirsiniz. VSPackage yüklendikten sonra, Seçenekler iletişim kutusunu açıp  klavye ortamı kategorisi altında komut yerleşimini düzenleyerek bu **komutları özelleştirebilirsiniz.** Bu bayrak kısayol menülerine, araç çubuklarına, menü denetleyicilerine veya alt menülere yerleştirmeyi etkilemez.<br /><br /> Şu için geçerlidir: `Button` , `Combo`|
|DefaultDisabled|Varsayılan olarak, bunu uygulayan VSPackage yüklenmezse veya yöntemi çağrılmasa `QueryStatus` komut devre dışı bırakılır.<br /><br /> Şu için geçerlidir: `Button` , `Combo`|
|DefaultDocked|Varsayılan olarak yerleştirildi. Bu ayar her zaman yerleştirildikleri için artık araç çubukları için geçerli değil.|
|DefaultInvisible|Varsayılan olarak, bunu uygulayan VSPackage yüklenmezse veya yöntemi çağrılmasa `QueryStatus` komut görünmez.<br /><br /> Bunu bayrağıyla birleştirmenizi `DynamicVisibility` öneririz.<br /><br /> Şu için geçerlidir: `Button` , `Combo` , `Menu`|
|DontCache|Geliştirme ortamı bu komut için `QueryStatus` yöntem sonuçlarını önbelleğe alınmaz.<br /><br /> Bir menü için bu, menü denetleyicisine menü öğelerinin metnini önbelleğe alınmamalarını söyler. Menüde dinamik öğeler veya dinamik metin içeren öğeler olduğunda bu bayrağı kullanın.<br /><br /> Şu için geçerlidir: `Button` , `Menu`|
|DynamicItemStart|Dinamik listenin başlangıcını gösterir. Bu, OLECMDERR_E_UNSUPPORTED bayrağı döndürülene kadar liste öğelerinde yöntemini tekrar `QueryStatus` tekrar çağırarak ortamın bir OLECMDERR_E_UNSUPPORTED sağlar. Bu, en son kullanılan (MRU) listeleri ve pencere listeleri gibi öğeler için iyi çalışır.<br /><br /> Şu için geçerlidir: `Button`|
|DynamicVisibility|Komutun görünürlüğü yöntemi aracılığıyla veya `QueryStatus` bölümüne dahil edilen bir bağlam GUID'si aracılığıyla `VisibilityConstraints` değiştirilebilir.<br /><br /> Menülerde ve araç penceresi araç çubuklarında görünen, ancak ana pencerede görünen üst düzey araç çubuklarında olmayan komutlar için geçerlidir. En üst düzey araç çubuğu öğeleri devre dışı bırakılabilir, ancak OLECMDF_INVISIBLE bayrağı yönteminden `QueryStatus` döndürüldü. Araç penceresi araç çubuklarında görünen araç çubuğu komutları gizlenebiliyor.<br /><br /> Bir menüde, bu bayrak tüm üyeleri gizlenirken otomatik olarak gizlenir gerektiğini de gösterir. Üst düzey menüler zaten bu davranışa sahip olduğundan bu bayrak genellikle alt menülere atanır.<br /><br /> Bu bayrağın bayrağıyla birleştirilmiş olması `DefaultInvisible` gerekir.<br /><br /> Şu için geçerlidir: `Button` , `Combo` , `Menu`|
|FilterKeys|Combo Öğesi altındaki Filtreleme Anahtarları [konu başlığına bakın.](../extensibility/combo-element.md)<br /><br /> Şu için geçerlidir: `Combo`|
|FixMenuController|Bu komut bir menü denetleyicisinde konumlandı ise, komut her zaman varsayılandır; diğer bir ifadeyle, menü denetleyicisi düğmesinin kendisi seçildiğinde komut seçilir. Menü denetleyicisinde bayrak `TextIsAnchorCommand` ayarlanmışsa, menü denetleyicisi bayrağı olan komuttan metnini de `FixMenuController` alır.<br /><br /> Menü denetleyicisinde yalnızca bir komut bayrağına sahip `FixMenuController` olmalıdır. Birden fazla komut bu şekilde işaretlenirse, menüye son komut varsayılan komut olur.<br /><br /> Şu için geçerlidir: `Button`|
|IconAndText|Menü ve araç çubuğunda bir simge ve metin gösterme.<br /><br /> Şu için geçerlidir: `Button` , `Combo` , `Menu`|
|NoAutoComplete|Otomatik tamamlama özelliği devre dışı bırakıldı.<br /><br /> Şu için geçerlidir: `Combo`|
|NoButtonCustomize|Kullanıcının bu düğmeyi özelleştirmesine izin verme.<br /><br /> Şu için geçerlidir: `Button` , `Combo`|
|NoKeyCustomize|Klavye özelleştirmesini etkinleştirme.<br /><br /> Şu için geçerlidir: `Button` , `Combo`|
|NoShowOnMenuController|Bu komut bir menü denetleyicisinde konumlandı ise, komut açılan listede görünmez.<br /><br /> Şu için geçerlidir: `Button`|
|NotInTBList|Kullanılabilir araç çubukları listesinde görünmez. Bu yalnızca Araç Çubuğu menü türleri için geçerlidir.<br /><br /> Şu için geçerlidir: `Menu`|
|NoToolbarClose|Kullanıcı araç çubuğunu kapatamaz. Bu yalnızca Araç Çubuğu menü türleri için geçerlidir.<br /><br /> Şu için geçerlidir: `Menu`|
|Pıct|Araç çubuğunda yalnızca bir simgeyi, ancak bir menüyü yalnızca metin olarak gösterir. Simge belirtilmezse, araç çubuğunda tıklanabilir boş alan gösterilir.<br /><br /> Şu için geçerlidir: `Button`|
|PostExec|Komutu engellemez. Geliştirme ortamı, tüm ön işleme sorguları tamamlanana kadar yürütmeyi önler.<br /><br /> Şu için geçerlidir: `Button`|
|RouteToDocs|Komut etkin belgeye yönlendirildi.<br /><br /> Şu için geçerlidir: `Button`|
|StretchHorizontally|Bu bayrak ayarlandığında, Genişlik Birleşik giriş kutusunun en düşük genişliği olur ve araç çubuğunda yer varsa, Birleşik giriş kutusu kullanılabilir alanı dolduracak şekilde uzatılır. Bu yalnızca araç çubuğu yatay olarak yuvalanmışsa ve araç çubuğunda yalnızca bir açılan kutu bayrağını kullanıyorsa oluşur (bayrak ilk Birleşik giriş kutusu hariç tüm üzerinde yok sayılır).<br /><br /> Geçerli: `Combo`|
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
