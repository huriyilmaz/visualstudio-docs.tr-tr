---
title: Verileri güncelleştirmek için LINQ to SQL depolanan yordamları kullanın
description: Verileri güncelleştirme, ekleme ve silme işlemlerini gerçekleştirmek için LINQ to SQL Nesne İlişkisel Tasarımcısı (O/R Designer) içindeki saklı yordamları kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5915de290a84429878eccb4eae17821f8ac27f70
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436419"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)

Saklı yordamlar **O/R tasarımcısına** eklenebilir ve tipik yöntemler olarak yürütülürler <xref:System.Data.Linq.DataContext> . Ayrıca, değişiklikler varlık sınıflarından veritabanına kaydedildiğinde ekleme, güncelleştirme ve silme işlemlerini gerçekleştiren varsayılan LINQ to SQL çalışma zamanı davranışını geçersiz kılmak için de kullanılabilir (örneğin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi çağırırken).

> [!NOTE]
> Saklı yordamınız istemciye geri gönderilmesi gereken değerler döndürürse (örneğin, saklı yordamda hesaplanan değerler), saklı yordamlarınızda çıkış parametreleri oluşturun. Çıkış parametrelerini kullanıdıysanız, O/R Tasarımcısı tarafından oluşturulan geçersiz kılmalara güvenmek yerine kısmi bir yöntem uygulamasını yazın. Veritabanı tarafından oluşturulan değerlerle eşlenen üyelerin ekleme veya GÜNCELLEŞTIRME işlemleri başarıyla tamamlandıktan sonra uygun değerlere ayarlanması gerekir. Daha fazla bilgi için, [varsayılan davranışı geçersiz kılan geliştiricinin sorumluluklarına](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)bakın.

> [!NOTE]
> LINQ to SQL kimlik (otomatik artış), ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve zaman damgası sütunları için veritabanı tarafından oluşturulan değerleri otomatik olarak işler. Diğer sütun türlerindeki veritabanı tarafından oluşturulan değerler beklenmedik bir şekilde null değer oluşmasına neden olur. Veritabanı tarafından oluşturulan değerleri döndürmek için, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> **true** ve şunlardan birine el ile ayarlamanız gerekir <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : [oto Sync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [oto Sync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)veya [oto Sync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Bir varlık sınıfının güncelleştirme davranışını yapılandırma

Varsayılan olarak, bir veritabanını güncelleştirme mantığı (ekler, güncelleştirmeler ve siler) LINQ to SQL varlık sınıflarında verilerde yapılan değişikliklerle birlikte LINQ to SQL çalışma zamanı tarafından sağlanır. Çalışma zamanı, tablonun şemasını temel alan varsayılan INSERT, UPDATE ve DELETE komutlarını oluşturur (sütun ve birincil anahtar bilgileri). Varsayılan davranış istenmiyorsa, tablonuzdaki verileri işlemek için gerekli olan ekleme, güncelleştirme ve silme işlemlerini gerçekleştirmek için belirli saklı yordamları atayarak güncelleştirme davranışını yapılandırabilirsiniz. Bunun yanı sıra, varsayılan davranış oluşturulmayan, örneğin varlık sınıflarınız görünümlerle eşlenme olduğunda da yapabilirsiniz. Son olarak, veritabanı saklı yordamlar üzerinden tablo erişimi gerektirdiğinde varsayılan güncelleştirme davranışını geçersiz kılabilirsiniz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Bir varlık sınıfının varsayılan davranışını geçersiz kılmak üzere saklı yordamlar atamak için

1. Tasarımcıda **LINQ to SQL** dosyasını açın. ( **Çözüm Gezgini** **. dbml** dosyasına çift tıklayın.)

2. **Sunucu Gezgini** veya **veritabanı Gezgini** ' de, **saklı yordamlar** ' ı genişletin ve varlık sınıfının INSERT, Update ve/veya delete komutları için kullanmak istediğiniz saklı yordamları bulun.

3. Saklı yordamı **O/R tasarımcısına** sürükleyin.

     Saklı yordam Yöntemler bölmesine Yöntem olarak eklenir <xref:System.Data.Linq.DataContext> . Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Güncelleştirme gerçekleştirmek için saklı yordamı kullanmak istediğiniz varlık sınıfını seçin.

5. **Özellikler** penceresinde, geçersiz kılmak için komutu seçin ( **Insert** , **Update** veya **Delete** ).

6. **Çalışma zamanı kullan** **iletişim kutusunu** açmak için sözcüklerin yanındaki üç nokta (...) simgesine tıklayın.

7. **Özelleştir** 'i seçin.

8. **Özelleştir** listesinde istenen saklı yordamı seçin.

9. Yöntem bağımsız değişkenlerinin ilgili **sınıf özellikleriyle** **eşlendiğini doğrulamak** için **Yöntem bağımsız değişkenlerinin** ve **Sınıf özelliklerinin** listesini inceleyin. Ve komutları için özgün Yöntem bağımsız değişkenlerini ( `Original_<ArgumentName>` ) özgün özelliklerine () eşleyin `<PropertyName> (Original)` `Update` `Delete` .

    > [!NOTE]
    > Varsayılan olarak, yöntem bağımsız değişkenleri, adlar eşleşiyorsa sınıf özellikleriyle eşlenir. Değiştirilen özellik adları, tablo ve varlık sınıfı arasında artık eşleşmezse, tasarımcı doğru eşlemeyi belirleyememesi durumunda eşlenecek eşdeğer sınıf özelliğini seçmeniz gerekebilir.

10. **Tamam** ' a veya **Uygula** ' ya tıklayın.

    > [!NOTE]
    > Her bir değişiklik yaptıktan sonra **Uygula** ' ya tıkladığınızda her bir sınıf ve davranış birleşimine yönelik davranışı yapılandırmaya devam edebilirsiniz. **Uygula** ' ya tıklamadan önce sınıfı veya davranışı değiştirirseniz, bir uyarı iletişim kutusu görüntülenir ve yaptığınız değişiklikleri uygulamak için size bir fırsat sağlar.

Güncelleştirmeler için varsayılan çalışma zamanı mantığını kullanmaya dönmek için, **Özellikler** penceresinde **Ekle** , **Güncelleştir** ve **Sil** komutunun yanındaki üç noktaya tıklayın ve sonra **davranışı Yapılandır** iletişim kutusunda **çalışma zamanını kullan** iletişim kutusunu seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext metotları](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Ekleme, güncelleştirme ve silme işlemleri (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
