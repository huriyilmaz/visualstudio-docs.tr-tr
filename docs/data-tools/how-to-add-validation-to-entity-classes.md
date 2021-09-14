---
title: 'Nasıl yapılır: Varlık sınıflarına doğrulama ekleme'
description: Varlık sınıflarında doğrulama eklemeyi gözden geçirme. Belirli bir sütundaki bir değere yapılan değişiklikler için doğrulama ekleyin. Varlık sınıfına güncelleştirmeler için doğrulama ekleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8103dc746d09f63fadeb536fea552db7b4baf7f0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631358"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Nasıl yapılır: Varlık sınıflarına doğrulama ekleme
*Varlık sınıflarını* doğrulama, veri nesnelerine girilen değerlerin bir nesnenin şemasında yer alan kısıtlamalara ve ayrıca uygulama için kurulan kurallara uygun olduğunu doğrulama işlemidir. Temel alınan veritabanına güncelleştirme göndermeden önce verileri doğrulama, hataları azaltan iyi bir uygulamadır. Ayrıca uygulama ile veritabanı arasındaki gidiş dönüş sayısını da azaltır.

[Visual Studio'daki](../data-tools/linq-to-sql-tools-in-visual-studio2.md) LINQ to SQL araçları, kullanıcıların tüm varlıkların Ekleme, Güncelleştirme ve Silmeleri sırasında ve ayrıca tek tek sütun değişiklikleri sırasında ve sonrasında çalışan tasarımcı tarafından oluşturulan kodu genişletmesini sağlayan kısmi yöntemler sağlar.

> [!NOTE]
> Bu konu, **O/R** Tasarımcısı kullanarak varlık sınıflarında doğrulama eklemeye yardımcı olacak temel adımları sağlar. Bu genel adımları belirli bir varlık sınıfına başvurulmadan takip etmek zor olabileceği için, gerçek verileri kullanan bir kılavuz sağlanır.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Belirli bir sütundaki değere yapılan değişiklikler için doğrulama ekleme
Bu yordam, bir sütundaki değer değişirken verilerin nasıl doğrulanmasına olanak sağlar. Doğrulama sınıf tanımı içinde (kullanıcı arabirimi yerine) gerçekleştirile olduğundan, değer doğrulamanın başarısız olması için bir özel durum oluşturur. Uygulamanıza sütun değerlerini değiştirmeye çalışan kod için hata işlemeyi uygulama.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Bir sütunun değer değişikliği sırasında verileri doğrulamak için

1. **O/R** Tasarımcısı'nda LINQ to SQL Classes dosyasını (**.dbml** dosyası) açın veya yeni bir oluşturun. (dosyanın içinde **.dbml** dosyasına **çift Çözüm Gezgini.)**

2. **O/R Tasarımcısı'nda,** doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve ardından Kodu **Görüntüle'ye tıklayın.**

     Kod Düzenleyicisi, seçilen varlık sınıfı için kısmi bir sınıfla açılır.

3. İmleci kısmi sınıfa yerleştirin.

4. Diğer Visual Basic için:

    1. Yöntem **Adı listesini** genişletin.

    2. Doğrulama eklemek **istediğiniz sütun için OnCOLUMNNAMEChanging** yöntemini bulun.

    3. Kısmi `OnCOLUMNNAMEChanging` sınıfa bir yöntem eklenir.

    4. Önce bir değerin girilir olduğunu doğrulamak ve ardından sütun için girilen değerin uygulamanız için kabul edilebilir olduğundan emin olmak için aşağıdaki kodu ekleyin. bağımsız `value` değişkeni önerilen değeri içerir, bu nedenle geçerli bir değer olduğunu onaylamak için mantık ekleyin:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    C# projeleri için:

    C# projeleri otomatik olarak olay işleyicileri oluşturmaz, intelliSense kullanarak sütun değiştiren kısmi yöntemleri oluşturabilirsiniz. Kullanılabilir `partial` kısmi yöntemler listesine erişmek için bir boşluk yazın ve ardından. Doğrulama eklemek istediğiniz sütunun sütun değiştirme yöntemine tıklayın. Aşağıdaki kod, sütun değiştirme kısmi yöntemini seçmenizde oluşturulan koda benzer:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Entity Sınıfına Güncelleştirmeler için Doğrulama Ekleme
Değişiklikler sırasında değerleri denetlemeye ek olarak, tam bir varlık sınıfını güncelleştirme girişiminde de veri doğrulanabilir. Denenen güncelleştirme sırasında doğrulama, iş kurallarının bunu gerektirmesi durumda birden çok sütunda yer alan değerleri karşılaştırmaya olanak sağlar. Aşağıdaki yordamda, tam bir varlık sınıfını güncelleştirmek için ne zaman deneme yapılır?

> [!NOTE]
> Varlık sınıflarını tamamlamak için güncelleştirmeler için doğrulama kodu kısmi sınıfta yürütülür (belirli bir varlık sınıfının kısmi <xref:System.Data.Linq.DataContext> sınıfı yerine).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Varlık sınıfına güncelleştirme sırasında verileri doğrulamak için

1. **O/R** Tasarımcısı'nda LINQ to SQL Classes dosyasını (**.dbml** dosyası) açın veya yeni bir oluşturun. (dosyanın içinde **.dbml** dosyasına **çift Çözüm Gezgini.)**

2. **O/R** Tasarımcısı'nda boş bir alana sağ tıklayın ve Kodu **Görüntüle'ye tıklayın.**

     Kod Düzenleyicisi, için kısmi bir sınıf ile `DataContext` açılır.

3. İmleci için kısmi sınıfa `DataContext` yerleştirin.

4. Diğer Visual Basic için:

    1. Yöntem **Adı listesini** genişletin.

    2. **UpdateENTITYCLASSNAME 'e tıklayın.**

    3. Kısmi `UpdateENTITYCLASSNAME` sınıfa bir yöntem eklenir.

    4. Aşağıdaki kodda gösterildiği gibi bağımsız `instance` değişkenlerini kullanarak tek tek sütun değerlerine erişin:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    C# projeleri için:

    C# projeleri otomatik olarak olay işleyicileri oluşturmaz, kısmi yöntemi oluşturmak için IntelliSense `UpdateCLASSNAME` kullanabilirsiniz. Kullanılabilir `partial` kısmi yöntemler listesine erişmek için bir boşluk yazın ve ardından. Doğrulama eklemek istediğiniz sınıfın güncelleştirme yöntemine tıklayın. Aşağıdaki kod, kısmi bir yöntem seçerek oluşturulan koda `UpdateCLASSNAME` benzer:

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

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Verileri doğrulama](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
