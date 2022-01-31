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
ms.openlocfilehash: ab0b3812dd17ee742e2c5d7c7ceabd347164bffb
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887105"
---
# <a name="command-flag-element"></a>Komut bayrağı öğesi
Üst öğesini değiştiren.

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
|CommandWellOnly|Komut üst düzey menüde görünmüyorsa ve ek kabuk özelleştirmesi için kullanılabilir hale (örneğin, bir klavye kısayolu bağlama gibi) bu bayrağı uygulayabilirsiniz. VSPackage yüklendikten sonra, Seçenekler iletişim kutusunu açıp klavye ortamı kategorisi altında komut yerleşimini düzenleyerek bu **komutları özelleştirebilirsiniz**. Bu bayrak kısayol menüleri, araç çubukları, menü denetleyicileri veya alt menülerin yerleşimini etkilemez.<br /><br /> Şu için geçerlidir: `Button`, `Combo`|
|DefaultDisabled|Varsayılan olarak, bunu uygulayan VSPackage yüklenmezse `QueryStatus` veya yöntemi çağrılmasa komut devre dışı bırakılır.<br /><br /> Şu için geçerlidir: `Button`, `Combo`|
|DefaultDocked|Varsayılan olarak yerleştirildi. Bu ayar her zaman yerleştirildikleri için artık araç çubukları için geçerli değil.|
|DefaultInvisible|Varsayılan olarak, bunu uygulayan VSPackage yüklenmezse `QueryStatus` veya yöntemi çağrılmasa komut görünmez.<br /><br /> Bunu bayrağıyla birleştirmenizi `DynamicVisibility` öneririz.<br /><br /> Şu için geçerlidir: `Button`, `Combo`, `Menu`|
|DontCache|Geliştirme ortamı, bu komut için `QueryStatus` yöntem sonuçlarını önbelleğe alınmaz.<br /><br /> Bu, bir menü denetleyicisine menü öğelerinin metnini önbelleğe eklemesini söyler. Menüde dinamik öğeler veya dinamik metin içeren öğeler olduğunda bu bayrağı kullanın.<br /><br /> Şu için geçerlidir: `Button`, `Menu`|
|DynamicItemStart|Dinamik listenin başlangıcını gösterir. Bu, OLECMDERR_E_UNSUPPORTED bayrağı döndürülene `QueryStatus` kadar liste öğelerinde yöntemini tekrar tekrar çağırarak ortamın bir OLECMDERR_E_UNSUPPORTED sağlar. Bu, en son kullanılan (MRU) listeleri ve pencere listeleri gibi öğeler için iyi çalışır.<br /><br /> Şu için geçerlidir: `Button`|
|DynamicVisibility|Komutun görünürlüğü yöntemi aracılığıyla veya `QueryStatus` bölümüne dahil edilen bir bağlam GUID'si aracılığıyla `VisibilityConstraints` değiştirilebilir.<br /><br /> Menülerde ve araç penceresi araç çubuklarında görünen, ancak ana pencerede görünen üst düzey araç çubuklarında olmayan komutlar için geçerlidir. En üst düzey araç çubuğu öğeleri devre dışı bırakılabilir, ancak OLECMDF_INVISIBLE bayrağı yönteminden döndürüldü `QueryStatus` . Araç penceresi araç çubuklarında görünen araç çubuğu komutları gizlenebiliyor.<br /><br /> Bir menüde, bu bayrak tüm üyeleri gizlenirken otomatik olarak gizlenir gerektiğini de gösterir. Üst düzey menüler zaten bu davranışa sahip olduğundan bu bayrak genellikle alt menülere atanır.<br /><br /> Bu bayrağın bayrağıyla birleştirilmiş olması `DefaultInvisible` gerekir.<br /><br /> Şu için geçerlidir: `Button`, `Combo`, `Menu`|
|FilterKeys|Birleşik Giriş Öğesi altındaki Filtreleme Anahtarları [konu başlığına bakın](../extensibility/combo-element.md).<br /><br /> Şu için geçerlidir: `Combo`|
|FixMenuController|Bu komut bir menü denetleyicisinde konumlandı ise, komut her zaman varsayılandır; diğer bir ifadeyle, menü denetleyicisi düğmesinin kendisi seçildiğinde komut seçilir. Menü denetleyicisinde bayrak ayarlanmışsa `TextIsAnchorCommand` , menü denetleyicisi bayrağı olan komuttan metnini de `FixMenuController` alır.<br /><br /> Menü denetleyicisinde yalnızca bir komut bayrağına sahip `FixMenuController` olmalıdır. Birden fazla komut bu şekilde işaretlenirse, menüye son komut varsayılan komut olur.<br /><br /> Şu için geçerlidir: `Button`|
|IconAndText|Menü ve araç çubuğunda bir simge ve metin gösterme.<br /><br /> Şu için geçerlidir: `Button`, `Combo`, `Menu`|
|NoAutoComplete|Otomatik tamamlama özelliği devre dışı bırakıldı.<br /><br /> Şu için geçerlidir: `Combo`|
|NoButtonCustomize|Kullanıcının bu düğmeyi özelleştirmesine izin verme.<br /><br /> Şu için geçerlidir: `Button`, `Combo`|
|NoKeyCustomize|Klavye özelleştirmesini etkinleştirme.<br /><br /> Şu için geçerlidir: `Button`, `Combo`|
|NoShowOnMenuController|Bu komut bir menü denetleyicisinde konumlandı ise, komut açılan listede görünmez.<br /><br /> Şu için geçerlidir: `Button`|
|NotInTBList|Kullanılabilir araç çubukları listesinde görünmez. Bu yalnızca Araç Çubuğu menü türleri için geçerlidir.<br /><br /> Şu için geçerlidir: `Menu`|
|NoToolbarClose|Kullanıcı araç çubuğunu kapatamaz. Bu yalnızca Araç Çubuğu menü türleri için geçerlidir.<br /><br /> Şu için geçerlidir: `Menu`|
|Pıct|Araç çubuğunda yalnızca bir simgeyi, ancak bir menüyü yalnızca metin olarak gösterir. Simge belirtilmezse, araç çubuğunda tıklanabilir boş alan gösterilir.<br /><br /> Şu için geçerlidir: `Button`|
|PostExec|Komutu engellemez. Geliştirme ortamı, tüm ön işleme sorguları tamamlanana kadar yürütmeyi önler.<br /><br /> Şu için geçerlidir: `Button`|
|RouteToDocs|Komut etkin belgeye yönlendirildi.<br /><br /> Şu için geçerlidir: `Button`|
|StretchHorizontally|Bu bayrak ayar olduğunda genişlik, birleşik giriş kutusu için en düşük genişlik haline gelir ve araç çubuğunda yer varsa birleşik giriş kutusu kullanılabilir alanı dolduracak şekilde esnetilebilir. Bu yalnızca araç çubuğu yatay olarak yerleştirildi ve araç çubuğundaki yalnızca bir birleşik giriş kutusu bayrağını kullanabilirse (bayrak ilk birleşik giriş kutusu dışında hepsinde yoksayılır) oluşur.<br /><br /> Şu için geçerlidir: `Combo`|
|TextChanges|Komut veya menü metni, genellikle yöntemi aracılığıyla çalışma zamanında `QueryStatus` değiştirilebilir.<br /><br /> Şu için geçerlidir: `Button`, `Menu`|
|TextChangesButton|Şu için geçerlidir: `Button`|
|TextIsAnchorCommand|Menü denetleyicisi için, menenin metni varsayılan (yer çubuğu) komutundan alınır. Sabit noktası komutu, seçilen veya kilitli son komut olandır. Bu bayrak ayarlanmazsa menü denetleyicisi kendi alanını `MenuText` kullanır. Ancak, menü denetleyicisine tıklarken ilgili denetleyiciden son seçilen komut yine de kullanılabilir.<br /><br /> Bu bayrağı bayrağıyla birleştirmenizi `TextChanges` öneririz.<br /><br /> Bu bayrak yalnızca MenuController veya MenuControllerLatched türünde menüler için geçerlidir.<br /><br /> Şu için geçerlidir: `Menu`|
|TextMenuCtrlUseMenu|Menü denetleyicilerinde `MenuText` alanını kullanın. Varsayılan alan' dır `ButtonText`.<br /><br /> Şu için geçerlidir: `Button`|
|TextMenuUseButton|Menüler `ButtonText` için alanını kullanın. Varsayılan alan belirtilmişse `MenuText` alanıdır.<br /><br /> Şu için geçerlidir: `Button`|
|Textonly|Bir araç çubuğunda veya menüde yalnızca metin gösterir, ancak simge belirtilmiş olsa bile simge gösterilmez.<br /><br /> Şu için geçerlidir: `Button`|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Düğme öğesi öğeleri için [bir grup](../extensibility/button-element.md) sağlar.|
|[Menüler öğesi](../extensibility/menus-element.md)|VSPackage'ın uygulayan tüm menüleri tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu () seçin. Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
