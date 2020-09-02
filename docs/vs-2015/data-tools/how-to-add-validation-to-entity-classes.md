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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665990"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Nasıl yapılır: Varlık sınıflarına doğrulama ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varlık sınıflarını *doğrulamak* , veri nesnelerine girilen değerlerin bir nesnenin şemasındaki kısıtlamalara ve ayrıca uygulama için belirlenen kurallara uygun olduğunu onaylama işlemidir. Temel alınan veritabanına güncelleştirmeleri göndermeden önce verilerin doğrulanması, hataları azaltan iyi bir uygulamadır. Ayrıca, bir uygulama ve veritabanı arasındaki gidiş dönüşlerin olası sayısını azaltır.

 [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , kullanıcıların, tüm varlıkların ekleme, güncelleştirme ve silme sırasında çalışan tasarımcı tarafından oluşturulan kodu genişletmelerine imkan tanıyan kısmi yöntemler sağlar ve ayrıca tek tek sütun değişiklikleri sırasında ve sonrasında.

> [!NOTE]
> Bu konu, kullanarak varlık sınıflarına doğrulama eklemeye yönelik temel adımları sağlar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Belirli bir varlık sınıfına başvurulmadan bu genel adımların izlenmesi zor olabileceğinden, gerçek verileri kullanan bir anlatım sağlanmış olur.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Belirli bir sütundaki değerde yapılan değişiklikler için doğrulama ekleme
 Bu yordam, bir sütundaki değer değiştiğinde verilerin nasıl doğrulandığını gösterir. Doğrulama sınıf tanımı içinde yapıldığından (Kullanıcı arabirimi yerine), değer doğrulamanın başarısız olmasına neden olursa bir özel durum oluşturulur. Uygulamanızda sütun değerlerini değiştirmeye çalışır olan kod için hata işlemeyi uygulayın.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Bir sütunun değer değişikliği sırasında verileri doğrulamak için

1. İçinde yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . ( **Çözüm Gezgini** **. dbml** dosyasına çift tıklayın.)

2. O/R tasarımcısında, doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

    Kod Düzenleyicisi seçili varlık sınıfı için kısmi bir sınıf ile açılır.

3. İmleci kısmi sınıfa yerleştirin.

4. Visual Basic projeleri için:

   1. **Yöntem adı** listesini genişletin.

   2. Doğrulamayı eklemek **On**istediğiniz sütun için_COLUMNNAME_**değiştirme** yöntemini bulun.

   3. `On` *COLUMNNAME* `Changing` Partial sınıfına bir COLUMNNAME yöntemi eklenir.

   4. Önce bir değer girildiğini doğrulamak ve ardından sütun için girilen değerin uygulamanız için kabul edilebilir olduğundan emin olmak için aşağıdaki kodu ekleyin. `value`Bağımsız değişken önerilen değeri içerir, bu nedenle geçerli bir değer olduğunu onaylamak için mantık ekleyin:

      ```vb
      If value.HasValue Then
          ' Add code to ensure that the value is acceptable.
          ' If value < 1 Then
          '    Throw New Exception("Invalid data!")
          ' End If
      End If
      ```

      C# projeleri için:

   5. C# projeleri otomatik olarak olay işleyicilerini oluşturmadığından, sütun değiştiren kısmi Yöntemler oluşturmak için IntelliSense 'i kullanabilirsiniz.

       `partial`Kullanılabilir kısmi yöntemlerin listesine erişmek için bir boşluk yazın. Doğrulama eklemek istediğiniz sütun için sütun değiştirme yöntemine tıklayın. Aşağıdaki kod, bir sütun değiştirme kısmi yöntemi seçtiğinizde oluşturulan koda benzer:

      ```csharp
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
          {
             throw new System.NotImplementedException();
          }

      ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Bir varlık sınıfına güncelleştirmeler için doğrulama ekleme
 Değişiklikler sırasında değerleri denetlemenin yanı sıra, bir bütün varlık sınıfını güncelleştirmek için bir deneme yapıldığında verileri de doğrulayabilirsiniz. Denenen bir güncelleştirme sırasında doğrulama, iş kuralları için gerekliyse, birden fazla sütundaki değerleri karşılaştırmanıza olanak sağlar. Aşağıdaki yordamda, bir bütün varlık sınıfını güncelleştirmek için bir girişim yapıldığında nasıl doğrulanacağı gösterilmektedir.

> [!NOTE]
> Varlık sınıflarının tamamlanma güncelleştirmeleri için doğrulama kodu, kısmi <xref:System.Data.Linq.DataContext> sınıfta yürütülür (belirli bir varlık sınıfının parçalı sınıfında yerine).

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Bir varlık sınıfına yönelik bir güncelleştirme sırasında verileri doğrulamak için

1. İçinde yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . ( **Çözüm Gezgini** **. dbml** dosyasına çift tıklayın.)

2. O/R tasarımcısında boş bir alana sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

    Kod Düzenleyicisi, için kısmi bir sınıf ile açılır `DataContext` .

3. İmleci için kısmi sınıfa yerleştirin `DataContext` .

4. Visual Basic projeleri için:

   1. **Yöntem adı** listesini genişletin.

   2. _Entityclassname_'ı **Güncelleştir**'e tıklayın.

   3. `Update`Kısmi sınıfa bir *entityclassname* yöntemi eklenir.

   4. `instance`Aşağıdaki kodda gösterildiği gibi bağımsız değişkenini kullanarak ayrı sütun değerlerine erişin:

      ```vb
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
          Dim ErrorMessage As String = "Invalid data!"
          Throw New Exception(ErrorMessage)
      End If
      ```

      C# projeleri için:

   5. C# projeleri otomatik olarak olay işleyicilerini oluşturmadığından, kısmi ClassName metodunu oluşturmak için IntelliSense 'i kullanabilirsiniz `Update` *CLASSNAME* .

   6. `partial`Kullanılabilir kısmi yöntemlerin listesine erişmek için bir boşluk yazın. Doğrulama eklemek istediğiniz sınıf için Update metoduna tıklayın. Aşağıdaki kod, `Update` *ClassName* kısmi yöntemini seçtiğinizde oluşturulan koda benzer:

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
