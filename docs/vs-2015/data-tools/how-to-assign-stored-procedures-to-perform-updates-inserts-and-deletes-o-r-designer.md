---
title: 'Nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609976"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Saklı yordamlar O/R tasarımcısına eklenebilir ve tipik yöntemler olarak yürütülürler <xref:System.Data.Linq.DataContext> . Ayrıca, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] değişiklikler varlık sınıflarından veritabanına kaydedildiğinde ekleme, güncelleştirme ve silme işlemlerini gerçekleştiren varsayılan çalışma zamanı davranışını geçersiz kılmak için de kullanılabilir (örneğin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi çağırırken).

> [!NOTE]
> Saklı yordamınız istemciye geri gönderilmesi gereken değerler döndürürse (örneğin, saklı yordamda hesaplanan değerler), saklı yordamlarınızda çıkış parametreleri oluşturun. Çıkış parametrelerini kullanıdıysanız, O/R Tasarımcısı tarafından oluşturulan geçersiz kılmalara güvenmek yerine kısmi bir yöntem uygulamasını yazın. Veritabanı tarafından oluşturulan değerlerle eşlenen üyelerin ekleme veya GÜNCELLEŞTIRME işlemleri başarıyla tamamlandıktan sonra uygun değerlere ayarlanması gerekir. Daha fazla bilgi için, [varsayılan davranışı geçersiz kılan geliştiricinin sorumluluklarına](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1)bakın.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] kimlik (otomatik artış), ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve zaman damgası sütunları için veritabanı tarafından oluşturulan değerleri otomatik olarak işler. Diğer sütun türlerindeki veritabanı tarafından oluşturulan değerler beklenmedik bir şekilde null değer oluşmasına neden olur. Veritabanı tarafından oluşturulan değerleri döndürmek için, aşağıdakilerden birine el ile ve olarak ayarlamanız gerekir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : <xref:System.Data.Linq.Mapping.AutoSync> , <xref:System.Data.Linq.Mapping.AutoSync> veya <xref:System.Data.Linq.Mapping.AutoSync> .

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Bir varlık sınıfının güncelleştirme davranışını yapılandırma
 Varsayılan olarak, varlık sınıflarında verilerde yapılan değişikliklerle bir veritabanını güncelleştirme mantığı (ekler, güncelleştirmeler ve siler) [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] çalışma zamanı tarafından sağlanır. Çalışma zamanı, tablonun şemasını temel alan varsayılan INSERT, Update ve DELETE komutlarını oluşturur (sütun ve birincil anahtar bilgileri). Varsayılan davranış istenmiyorsa, tablonuzdaki verileri işlemek için gerekli olan ekleme, güncelleştirme ve silme işlemlerini gerçekleştirmek için belirli saklı yordamları atayarak güncelleştirme davranışını yapılandırabilirsiniz. Bunun yanı sıra, varsayılan davranış oluşturulmayan, örneğin varlık sınıflarınız görünümlerle eşlenme olduğunda da yapabilirsiniz. Son olarak, veritabanı saklı yordamlar üzerinden tablo erişimi gerektirdiğinde varsayılan güncelleştirme davranışını geçersiz kılabilirsiniz.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Bir varlık sınıfının varsayılan davranışını geçersiz kılmak üzere saklı yordamlar atamak için

1. Tasarımcıda **LINQ to SQL** dosyasını açın. ( **Çözüm Gezgini**. dbml dosyasına çift tıklayın.)

2. **Sunucu Gezgini** / **veritabanı Gezgini**, **saklı yordamlar** ' ı genişletin ve varlık sınıfının INSERT, Update ve/veya delete komutları için kullanmak istediğiniz saklı yordamları bulun.

3. Saklı yordamı O/R tasarımcısına sürükleyin.

     Saklı yordam Yöntemler bölmesine Yöntem olarak eklenir <xref:System.Data.Linq.DataContext> . Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Güncelleştirme gerçekleştirmek için saklı yordamı kullanmak istediğiniz varlık sınıfını seçin.

5. **Özellikler** penceresinde, geçersiz kılmak için komutu seçin (**Insert**, **Update**veya **Delete**).

6. **Çalışma zamanı kullan** **iletişim kutusunu** açmak için sözcüklerin yanındaki üç nokta (...) simgesine tıklayın.

7. **Özelleştir**'i seçin.

8. **Özelleştir** listesinde istenen saklı yordamı seçin.

9. Yöntem bağımsız değişkenlerinin ilgili **sınıf özellikleriyle** **eşlendiğini doğrulamak** için **Yöntem bağımsız değişkenlerinin** ve **Sınıf özelliklerinin** listesini inceleyin. Update ve DELETE komutları için özgün Yöntem bağımsız değişkenlerini (Original_*ArgumentName*) orijinal özelliklerle (*PropertyName* (özgün)) eşleyin.

    > [!NOTE]
    > Varsayılan olarak, yöntem bağımsız değişkenleri, adlar eşleşiyorsa sınıf özellikleriyle eşlenir. Değiştirilen özellik adları, tablo ve varlık sınıfı arasında artık eşleşmezse, tasarımcı doğru eşlemeyi belirleyememesi durumunda eşlenecek eşdeğer sınıf özelliğini seçmeniz gerekebilir.

10. **Tamam** ' a veya **Uygula**' ya tıklayın.

    > [!NOTE]
    > Her bir değişiklik yaptıktan sonra **Uygula** ' ya tıkladığınızda her bir sınıf/davranış birleşiminin davranışını yapılandırmaya devam edebilirsiniz. **Uygula**' ya tıklamadan önce sınıfı veya davranışı değiştirirseniz, herhangi bir değişiklik uygulamaya fırsat sağlayan bir uyarı iletişim kutusu görüntülenir.

     Güncelleştirmeler için varsayılan çalışma zamanı mantığını kullanmaya dönmek için, **Özellikler** penceresinde Ekle, Güncelleştir ve Sil komutunun yanındaki üç noktaya tıklayın ve sonra **davranışı Yapılandır** Iletişim kutusunda **çalışma zamanını kullan** iletişim kutusunu seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [DataContext yöntemlerinde LINQ to SQL araçları (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) izlenecek yol: [Insert, Update ve DELETE Işlemlerine](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL sınıfları (o-r Designer) oluşturma](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
