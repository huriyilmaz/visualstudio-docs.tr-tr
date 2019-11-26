---
title: Değişiklikleri modelin dışına yayan olay Işleyicileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a23a8d28f336728789fe9cbbe38f965cc56763d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295519"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirme ve modelleme SDK 'sında mağaza dışı değişkenler, dosyalar, diğer mağazalardaki modeller veya diğer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantıları gibi mağaza dışındaki kaynaklara değişiklikleri yaymak için depo olay işleyicilerini tanımlayabilirsiniz. Mağaza olay işleyicileri, tetikleme olayının gerçekleştiği işlemin sonundan sonra yürütülür. Bunlar ayrıca bir geri alma veya yineleme işleminde yürütülür. Bu nedenle, mağaza kurallarından farklı olarak mağaza olayları, deponun dışındaki değerleri güncelleştirmek için en yararlı seçenektir. .NET olaylarının aksine, Store olay işleyicileri bir sınıfı dinlemek için kaydedilir: her örnek için ayrı bir işleyici kaydetmeniz gerekmez. Değişiklikleri işlemek için farklı yollar arasından nasıl seçim yapılacağı hakkında daha fazla bilgi için bkz. [yanıt verme ve yayma değişiklikleri](../modeling/responding-to-and-propagating-changes.md).

 Grafik yüzeyi ve diğer kullanıcı arabirimi denetimleri, depo olayları tarafından işlenebilen dış kaynak örnekleridir.

### <a name="to-define-a-store-event"></a>Bir mağaza olayını tanımlamak için

1. İzlemek istediğiniz olay türünü seçin. Tam liste için <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>özelliklerine bakın. Her özellik bir olay türüne karşılık gelir. En sık kullanılan olay türleri şunlardır:

   - `ElementAdded` – bir model öğesi, ilişki bağlantısı, şekil veya bağlayıcı oluşturulduğunda tetiklenir.

   - ElementPropertyChanged – bir `Normal` alanı özelliğinin değeri değiştiğinde tetiklenir. Olay yalnızca yeni ve eski değerler eşit değilse tetiklenir. Olay, hesaplanan ve özel depolama özelliklerine uygulanamaz.

        İlişki bağlantılarına karşılık gelen rol özelliklerine uygulanamaz. Bunun yerine, etki alanı ilişkisini izlemek için `ElementAdded` kullanın.

   - `ElementDeleted` – bir model öğesi, ilişki, şekil veya bağlayıcı silindikten sonra tetiklenir. Öğesinin özellik değerlerine erişmeye devam edebilirsiniz, ancak diğer öğelerle hiçbir ilişkisi olmayacaktır.

2. **DslPackage** projesindeki ayrı bir kod dosyasında, _yourdsl_**DocData** için kısmi bir sınıf tanımı ekleyin.

3. Aşağıdaki örnekte olduğu gibi olayın kodunu Yöntem olarak yazın. `DocData`erişmek istemediğiniz müddetçe `static`olabilir.

4. İşleyiciyi kaydetmek için `OnDocumentLoaded()` geçersiz kılın. Birden fazla işleyiciniz varsa, bunları aynı yerde kaydedebilirsiniz.

   Kayıt kodunun konumu önemli değil. `DocView.LoadView()` alternatif bir konumdur.

```
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
      base.OnDocumentLoaded(); // Don’t forget this.

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

## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>Depoda geri alınamaz ayarlamalar yapmak için olayları kullanma
 Olay işleyicisi işlem tamamlandıktan sonra yürütüldüğü için mağaza olayları normalde mağaza içindeki değişiklikleri yayılırken kullanılmaz. Bunun yerine, bir mağaza kuralı kullanırsınız. Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

 Ancak, kullanıcının ek güncelleştirmeleri özgün olaydan ayrı olarak geri almak istiyorsanız, depoya ek güncelleştirmeler yapmak için bir olay işleyicisi kullanabilirsiniz. Örneğin, küçük harf karakterlerinin albüm başlıkları için normal kural olduğunu varsayalım. Kullanıcı büyük harfe yazıldıktan sonra başlığı küçük harfe düzelten bir mağaza olay işleyicisi yazabilirsiniz. Ancak Kullanıcı, geri al komutunu kullanarak, büyük harf karakterlerini geri yükleyerek düzeltmeyi iptal edebilir. İkinci bir geri alma kullanıcının değişikliğini kaldırır.

 Buna karşılık, aynı şeyi yapmak için bir mağaza kuralı aldıysanız, kullanıcının değişikliği ve düzeltmesi aynı işlemde olur, böylece kullanıcı özgün değişikliği kaybetmeden ayarlamayı geri alamazsınız.

```

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

 Mağazayı güncelleştiren bir olay yazarsanız:

- Geri al 'da model öğelerinde değişiklik yapmaktan kaçınmak için `store.InUndoRedoOrRollback` kullanın. İşlem Yöneticisi depodaki her şeyi özgün durumuna geri ayarlayacaktır.

- Model dosyadan yüklenirken değişiklik yapmaktan kaçınmak için `store.InSerializationTransaction` kullanın.

- Değişiklikleriniz, daha fazla olayın tetiklenmesi için yol açacaktır. Sonsuz bir döngüden kaçındığınızdan emin olun.

## <a name="store-event-types"></a>Olay türlerini depola
 Her olay türü Store. EventManagerDirectory içindeki bir koleksiyona karşılık gelir. Herhangi bir zamanda olay işleyicileri ekleyebilir veya kaldırabilirsiniz, ancak belge yüklendiğinde bunları eklemek her zamanki gibi olur.

|`EventManagerDirectory` Özellik adı|Yürütüldüğünde yürütülür|
|-------------------------------------------|-------------------|
|ElementAdded|Bir etki alanı sınıfı, etki alanı ilişkisi, şekil, bağlayıcı veya Diyagram örneği oluşturulur.|
|ElementDeleted|Bir model öğesi deponun öğe dizininden kaldırıldı ve artık hiçbir ilişkinin kaynağı veya hedefi değil. Öğe gerçekten bellekten silinmez, ancak gelecekte geri alma durumunda tutulur.|
|Elementeventsbaşladı|Bir dış işlemin sonunda çağırılır.|
|ElementEventsEnded|Tüm diğer olaylar işlendiğinde çağrılır.|
|Elementtaşındı|Bir model öğesi bir depolama bölümünden diğerine taşındı.<br /><br /> Bu, diyagramdaki bir şeklin konumuyla ilgili değildir.|
|ElementPropertyChanged|Bir etki alanı özelliğinin değeri değişti. Bu, yalnızca eski ve yeni değerler eşit değilse yürütülür.|
|Roleplayerdeğişti|Bir ilişkinin iki rolünden biri (bitiyor), yeni bir öğeye başvurur.|
|RolePlayerOrderChanged|1 ' den büyük çokluğa sahip bir rolde, bağlantıların sırası değişmiştir.|
|Işlem başlangıcı||
|Işlem yürütüldü||
|TransactionRolledBack||

## <a name="see-also"></a>Ayrıca Bkz.
 [Değişikliklere Yanıt Verme ve Değişiklikleri Yayma](../modeling/responding-to-and-propagating-changes.md)
