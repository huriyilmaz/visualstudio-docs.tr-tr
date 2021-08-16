---
title: Verileri güncelleştirmek için LINQ to SQL yordamları kullanma
description: Veri güncelleştirmeleri, eklemeleri ve LINQ to SQL Nesne İlişkisel Tasarımcısı gerçekleştirmek için LINQ to SQL Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) içinde saklı yordamları kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 51cdb3f5af6f77d67cdcd9342e39aca6a5dcf24730cb9565ce5b0404b24e1543
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347174"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)

Saklı yordamlar **O/R Tasarımcısı'na eklenebilir ve** tipik yöntemler olarak <xref:System.Data.Linq.DataContext> yürütülebilirsiniz. Bunlar, varlık sınıflarından bir veritabanına (örneğin, yöntemi çağrılırken) kaydedildiklerinden Eklemeler, Güncelleştirmeler ve Silmeler gerçekleştiren varsayılan LINQ to SQL çalışma zamanı davranışını geçersiz kılmak için de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> kullanılabilir.

> [!NOTE]
> Saklı yordamınız istemciye geri gönderilecek değerleri döndürürse (örneğin, saklı yordamda hesaplanan değerler), saklı yordamlarınıza çıkış parametreleri oluşturun. Çıkış parametrelerini kullanasanız, O/R Tasarımcısı tarafından oluşturulan geçersiz kılmalara güvenmek yerine kısmi bir yöntem uygulaması yazın. INSERT veya UPDATE işlemleri başarıyla tamamlandıktan sonra, veritabanı tarafından oluşturulan değerlerle eşlenen üyelerin uygun değerlere ayarlanmış olması gerekir. Daha fazla bilgi için [bkz. Varsayılan Davranışı Geçersiz Kılmada Geliştiricinin Sorumlulukları.](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)

> [!NOTE]
> LINQ to SQL veritabanı tarafından oluşturulan değerleri kimlik (otomatik artırma), rowguidcol (veritabanı tarafından oluşturulan GUID) ve zaman damgası sütunları için otomatik olarak işlemeyi sağlar. Diğer sütun türlerinde veritabanı tarafından oluşturulan değerler beklenmedik şekilde null değere neden olur. Veritabanı tarafından oluşturulan değerleri geri dönmek için el ile true ve şu değerlerden biri olarak <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> ayarlamalısınız:  <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)veya [AutoSync.OnUpdate.](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Varlık Sınıfının Güncelleştirme Davranışını Yapılandırma

Varsayılan olarak, bir veritabanını (ekler, güncelleştirmeler ve silmeler) varlık sınıflarında verilerde yapılan değişikliklerle güncelleştirme mantığı LINQ to SQL çalışma zamanı tarafından LINQ to SQL sağlanır. Çalışma zamanı, tablonun şemasını (sütun ve birincil anahtar bilgileri) temel alan varsayılan INSERT, UPDATE ve DELETE komutları oluşturur. Varsayılan davranış istene geldiğinde, tablodaki verileri işlemek için gerekli eklemeleri, güncelleştirmeleri ve silmeleri gerçekleştirmek üzere belirli saklı yordamlar ataarak güncelleştirme davranışını yapılandırabilirsiniz. Bunu, varsayılan davranış oluşturulmazken de (örneğin, varlık sınıflarınızı görünümlere eşleye) de yapabiliriz. Son olarak, veritabanı saklı yordamlar aracılığıyla tablo erişimi gerektirdiğinde varsayılan güncelleştirme davranışını geçersiz kılabilirsiniz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Bir varlık sınıfının varsayılan davranışını geçersiz kılmak üzere saklı yordamlar atamak için

1. Tasarımcıda **LINQ to SQL** dosyasını açın. (dosyanın içinde **.dbml** dosyasına **çift Çözüm Gezgini.)**

2. Sunucu Gezgini  veya **Veritabanı Gezgini'da** Saklı Yordamlar'ı genişletin ve varlık sınıfının Ekle, Güncelleştir ve/veya Sil komutları için kullanmak istediğiniz saklı yordamları bulun. 

3. Saklı yordamı **O/R Tasarımcısı'na sürükleyin.**

     Saklı yordam yöntemler bölmesine bir yöntem olarak <xref:System.Data.Linq.DataContext> eklenir. Daha fazla bilgi için bkz. [DataContext Yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).

4. Güncelleştirmeleri gerçekleştirmek için saklı yordamı kullanmak istediğiniz varlık sınıfını seçin.

5. Özellikler penceresinde **geçersiz** kılınacak komutu seçin (**Ekle,** **Güncelleştir** veya **Sil).**

6. Davranışı Yapılandır iletişim kutusunu açmak için Çalışma Zamanı **Kullan** sözcüklerinin yanındaki üç **nokta (...) seçeneğine** tıklayın.

7. **Özelleştir**'i seçin.

8. Özelleştir listesinde istenen saklı **yordamı** seçin.

9. Yöntem Bağımsız **Değişkenleri'nin uygun** **Sınıf Özellikleri ile eş** olduğunu doğrulamak için **Yöntem** Bağımsız Değişkenleri ve Sınıf Özellikleri **listesini inceler.** Özgün yöntem bağımsız değişkenlerini ( `Original_<ArgumentName>` ) ve komutlarının özgün özelliklerine ( `<PropertyName> (Original)` ) `Update` `Delete` eşler.

    > [!NOTE]
    > Varsayılan olarak, adlar eşlence yöntem bağımsız değişkenleri sınıf özellikleriyle eşler. Değiştirilen özellik adları artık tablo ile varlık sınıfı arasında eşlenmeyecekse, tasarımcı doğru eşlemeyi belirleyemeyecekse eşlemek için eşdeğer sınıf özelliğini seçmeniz gerekir.

10. **Tamam'a veya** Uygula'ya **tıklayın.**

    > [!NOTE]
    > Her değişiklik sonrasında Uygula'ya tıklarken her sınıf ve davranış bileşimi **için** davranışı yapılandırmaya devam edersiniz. Uygula'ya tıklamadan önce sınıfı veya **davranışı** değiştirirsanız, bir uyarı iletişim kutusu görüntülenir ve değişikliklerinizi uygulama fırsatı sağlar.

Güncelleştirmeler için varsayılan çalışma zamanı mantığını kullanmaya geri dönmek için Özellikler  penceresinde **Ekle,** Güncelleştir veya  Sil komutunun yanındaki üç noktayı tıklatın ve ardından Davranışı Yapılandır iletişim kutusunda Çalışma zamanı **kullan'ı** seçin. 

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext metotları](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Ekleme, güncelleştirme ve silme işlemleri (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
