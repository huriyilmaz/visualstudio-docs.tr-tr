---
title: Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri
description: Görselleştirme ve Modelleme SDK'sı ile değişiklikleri mağazanın dışındaki kaynaklara yayma için mağaza olay işleyicileri tanımlayabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0617021a5184b3812a88c26dce2c142b1d769544
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027753"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri

Görselleştirme ve Modelleme SDK'sı'da mağaza dışındaki kaynaklara değişiklikleri yayan depo olay işleyicileri tanımlayabilirsiniz. Örneğin, depo dışı değişkenler, dosyalar, diğer depolarda bulunan modeller veya diğer Visual Studio uzantıları. Depolama olayı işleyicileri, tetikleyici olayın meydana geldiği işlem sona erdikten sonra yürütülür. Bunlar aynı zamanda Bir Geri Al veya Yinele işlemiyle yürütülür. Bu nedenle, depo kurallarının aksine, depo olayları en çok depo dışındaki değerleri güncelleştirmek için yararlıdır. .NET olaylardan farklı olarak, depo olay işleyicileri bir sınıfı dinlemek için kaydedilir: her örnek için ayrı bir işleyici kaydetmeye gerek yok. Değişiklikleri işlemenin farklı yolları arasında seçim yapmak hakkında daha fazla bilgi için bkz. Değişiklikleri [Yanıt verme ve Yayma.](../modeling/responding-to-and-propagating-changes.md)

Grafik yüzeyi ve diğer kullanıcı arabirimi denetimleri, depo olayları tarafından işilebilecek dış kaynaklara örnek olarak verilmiştir.

### <a name="to-define-a-store-event"></a>Mağaza olayı tanımlamak için

1. İzlemek istediğiniz olay türünü seçin. Tam liste için özelliklerine <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> bakın. Her özellik bir olay türüne karşılık gelen bir özelliktir. En sık kullanılan olay türleri:

    - `ElementAdded` - model öğesi, ilişki bağlantısı, şekil veya bağlayıcı oluşturulduğunda tetiklenir.

    - ElementPropertyChanged - bir etki alanı özelliğinin `Normal` değeri değiştirilse tetiklenir. Olay yalnızca yeni ve eski değerler eşit değilse tetiklenir. Olay hesaplanan ve özel depolama özelliklerine uygulanamaz.

         İlişki bağlantılarına karşılık gelen rol özelliklerine uygulanamaz. Bunun yerine, `ElementAdded` etki alanı ilişkisini izlemek için kullanın.

    - `ElementDeleted` - model öğesi, ilişki, şekil veya bağlayıcı silindikten sonra tetiklenir. Yine de öğenin özellik değerlerine erişebilirsiniz, ancak diğer öğelerle hiçbir ilişkisi olmaz.

2. **DslPackage** projesinde _ayrı bir kod dosyasına YourDsl_**DocData** için kısmi bir sınıf tanımı ekleyin.

3. Aşağıdaki örnekte olduğu gibi, olayın kodunu bir yöntem olarak yazın. Erişmek `static` istemiyorsanız `DocData` olabilir.

4. `OnDocumentLoaded()`İşleyiciyi kaydetmek için geçersiz kılın. Birden fazla işleyiciye sahipsanız, bunların hepsini aynı yere kaydedesiniz.

Kayıt kodunun konumu kritik değildir. `DocView.LoadView()` alternatif bir konum.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Mağazada Geri Alınabilir Ayarlamalar Yapmak için Olayları Kullanma

Olay işleyicisi, işlem işlendikten sonra yürütülür. Bunun yerine, bir mağaza kuralı kullanabilirsiniz. Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

Bununla birlikte, kullanıcının ek güncelleştirmeleri özgün olaydan ayrı olarak geri alamalarını istemeniz durumunda depoda ek güncelleştirmeler yapmak için bir olay işleyicisi kullanabilirsiniz. Örneğin, küçük harf karakterlerinin, başlık başlıkları için her zamanki kural olduğunu varsayalım. Kullanıcı büyük harfle yazdıktan sonra başlığı küçük harfe düzelten bir mağaza olay işleyicisi yazabilir. Ancak kullanıcı, büyük harf karakterlerini geri yükleyerek düzeltmenizi iptal etmek için Geri Al komutunu kullanabilir. İkinci bir Geri Alma işlemi kullanıcının değişikliklerini kaldırır.

Buna karşılık, aynı şeyi yapmak için bir mağaza kuralı yazarsanız, kullanıcının değişikliği ve düzeltmeniz aynı işlemde olur ve böylece kullanıcı özgün değişikliği kaybetmeden ayarlamayı geri alamaz.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Depoda güncelleştirmeler yapılan bir olay yazarsanız:

- Geri `store.InUndoRedoOrRollback` Alma'da model öğelerinde değişiklik yapmaktan kaçınmak için kullanın. İşlem yöneticisi, depoda yer alan her şeyi özgün durumuna geri ayarlar.

- Model `store.InSerializationTransaction` dosyadan yüklenirken değişiklik yapmaktan kaçınmak için kullanın.

- Değişiklikleriniz daha fazla olay tetiklenir. Sonsuz döngüden kaçının.

## <a name="store-event-types"></a>Olay türlerini depolama

Her olay türü Store.EventManagerDirectory'de bir koleksiyona karşılık gelen bir koleksiyondur. Olay işleyicilerini istediğiniz zaman ekleyebilir veya kaldırabilirsiniz, ancak belge yüklendiğinde bunları eklemek normaldir.

|`EventManagerDirectory` Özellik adı|Şu zaman yürütülür:|
|-|-|
|Elementadded|Bir etki alanı sınıfı, etki alanı ilişkisi, şekil, bağlayıcı veya diyagram örneği oluşturulur.|
|ElementDeleted|Model öğesi mağazanın öğe dizininden kaldırılmıştır ve artık hiçbir ilişkinin kaynağı veya hedefi değildir. öğesi bellekten silinmez, ancak gelecekteki bir Geri Alma durumunda korunur.|
|ElementEventsBegun|Dış işlem sonunda çağrılır.|
|ElementEventsEnded|Diğer tüm olaylar işlendiğinde çağrılır.|
|ElementMoved|Bir model öğesi bir mağaza bölümden diğerine taşındı.<br /><br /> Bu, diyagramda bir şeklin konumuyla ilgili değildir.|
|ElementPropertyChanged|Bir etki alanı özelliğinin değeri değişmiştir. Bu yalnızca eski ve yeni değerler eşitsizlikse yürütülür.|
|RolePlayerChanged|bir ilişkinin iki rolü (sona erer) biri yeni bir öğeye başvurur.|
|RolePlayerOrderChanged|Çokluğu 1'den büyük olan bir rolde bağlantı dizisi değişmiştir.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Ayrıca bkz.

- [Değişikliklere Yanıt Verme ve Değişiklikleri Yayma](../modeling/responding-to-and-propagating-changes.md)
- [Örnek kod: Devre Diyagramları](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
