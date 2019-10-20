---
title: 'Nasıl yapılır: varlık sınıflarına doğrulama ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a68b0314f3c64ce9196b8d48a78844bc81990a92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665990"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Nasıl yapılır: varlık sınıflarına doğrulama ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varlık sınıflarını *doğrulamak* , veri nesnelerine girilen değerlerin bir nesnenin şemasındaki kısıtlamalara ve ayrıca uygulama için belirlenen kurallara uygun olduğunu onaylama işlemidir. Temel alınan veritabanına güncelleştirmeleri göndermeden önce verilerin doğrulanması, hataları azaltan iyi bir uygulamadır. Ayrıca, bir uygulama ve veritabanı arasındaki gidiş dönüşlerin olası sayısını azaltır.

 [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , kullanıcıların, tüm varlıkların ekleme, güncelleştirme ve silme sırasında çalışan tasarımcı tarafından oluşturulan kodu genişletmelerine imkan tanıyan kısmi yöntemler sağlar ve ayrıca tek tek sütun değişiklikleri sırasında ve sonrasında.

> [!NOTE]
> Bu konuda, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] kullanarak varlık sınıflarına doğrulama eklemek için temel adımlar sağlanmaktadır. Belirli bir varlık sınıfına başvurulmadan bu genel adımların izlenmesi zor olabileceğinden, gerçek verileri kullanan bir anlatım sağlanmış olur.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Belirli bir sütundaki değerde yapılan değişiklikler için doğrulama ekleme
 Bu yordam, bir sütundaki değer değiştiğinde verilerin nasıl doğrulandığını gösterir. Doğrulama sınıf tanımı içinde yapıldığından (Kullanıcı arabirimi yerine), değer doğrulamanın başarısız olmasına neden olursa bir özel durum oluşturulur. Uygulamanızda sütun değerlerini değiştirmeye çalışır olan kod için hata işlemeyi uygulayın.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Bir sütunun değer değişikliği sırasında verileri doğrulamak için

1. @No__t_1 yeni bir LINQ to SQL Classes dosyası ( **. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** **. dbml** dosyasına çift tıklayın.)

2. O/R tasarımcısında, doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

    Kod Düzenleyicisi seçili varlık sınıfı için kısmi bir sınıf ile açılır.

3. İmleci kısmi sınıfa yerleştirin.

4. Visual Basic projeleri için:

   1. **Yöntem adı** listesini genişletin.

   2. Doğrulamayı eklemekistediğiniz sütun için_COLUMNNAME_**değiştirme** yöntemini bulun.

   3. Kısmi sınıfa `On` bir*COLUMNNAME* `Changing` yöntemi eklenir.

   4. Önce bir değer girildiğini doğrulamak ve ardından sütun için girilen değerin uygulamanız için kabul edilebilir olduğundan emin olmak için aşağıdaki kodu ekleyin. @No__t_0 bağımsız değişkeni önerilen değeri içerir, bu nedenle geçerli bir değer olduğunu onaylamak için mantık ekleyin:

      ```vb
      If value.HasValue Then
          ' Add code to ensure that the value is acceptable.
          ' If value < 1 Then
          '    Throw New Exception("Invalid data!")
          ' End If
      End If
      ```

      Projeler C# için:

   5. C# Projeler olay işleyicilerini otomatik olarak oluşturmadığından, sütun değiştiren kısmi Yöntemler oluşturmak için IntelliSense 'i kullanabilirsiniz.

       @No__t_0 yazın ve ardından kullanılabilir kısmi yöntemlerin listesine erişmek için bir boşluk girin. Doğrulama eklemek istediğiniz sütun için sütun değiştirme yöntemine tıklayın. Aşağıdaki kod, bir sütun değiştirme kısmi yöntemi seçtiğinizde oluşturulan koda benzer:

      ```csharp
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
          {
             throw new System.NotImplementedException();
          }

      ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Bir varlık sınıfına güncelleştirmeler için doğrulama ekleme
 Değişiklikler sırasında değerleri denetlemenin yanı sıra, bir bütün varlık sınıfını güncelleştirmek için bir deneme yapıldığında verileri de doğrulayabilirsiniz. Denenen bir güncelleştirme sırasında doğrulama, iş kuralları için gerekliyse, birden fazla sütundaki değerleri karşılaştırmanıza olanak sağlar. Aşağıdaki yordamda, bir bütün varlık sınıfını güncelleştirmek için bir girişim yapıldığında nasıl doğrulanacağı gösterilmektedir.

> [!NOTE]
> Varlık sınıflarının tamamlanma güncelleştirmeleri için doğrulama kodu, kısmi <xref:System.Data.Linq.DataContext> sınıfında (belirli bir varlık sınıfının parçalı sınıfında değil) yürütülür.

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Bir varlık sınıfına yönelik bir güncelleştirme sırasında verileri doğrulamak için

1. @No__t_1 yeni bir LINQ to SQL Classes dosyası ( **. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** **. dbml** dosyasına çift tıklayın.)

2. O/R tasarımcısında boş bir alana sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

    Kod Düzenleyicisi `DataContext` için bir kısmi sınıfla açılır.

3. İmleci `DataContext` kısmi sınıfına yerleştirin.

4. Visual Basic projeleri için:

   1. **Yöntem adı** listesini genişletin.

   2. _Entityclassname_'ı **Güncelleştir**'e tıklayın.

   3. Kısmi sınıfa bir `Update`*Entityclassname* yöntemi eklenir.

   4. Aşağıdaki kodda gösterildiği gibi `instance` bağımsız değişkenini kullanarak ayrı sütun değerlerine erişin:

      ```vb
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
          Dim ErrorMessage As String = "Invalid data!"
          Throw New Exception(ErrorMessage)
      End If
      ```

      Projeler C# için:

   5. C# Projeler olay işleyicilerini otomatik olarak oluşturmadığından, kısmi `Update`*ClassName* metodunu oluşturmak için IntelliSense 'i kullanabilirsiniz.

   6. @No__t_0 yazın ve ardından kullanılabilir kısmi yöntemlerin listesine erişmek için bir boşluk girin. Doğrulama eklemek istediğiniz sınıf için Update metoduna tıklayın. Aşağıdaki kod, bir `Update`*ClassName* kısmi yöntemi seçtiğinizde oluşturulan koda benzer:

      ```csharp
      partial void UpdateCLASSNAME(CLASSNAME instance)
      {
          if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
          {
              string ErrorMessage = "Invalid data!";
              throw new System.Exception(ErrorMessage);
          }
      }
      ```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçlar](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [verileri doğrulama](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
