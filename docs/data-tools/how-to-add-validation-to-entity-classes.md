---
title: 'Nasıl yapılır: Varlık sınıflarına doğrulama ekleme'
description: Varlık sınıflarına doğrulamanın nasıl ekleneceğini inceleyin. Belirli bir sütundaki bir değere yapılan değişiklikler için doğrulama ekleyin. Bir varlık sınıfına güncelleştirmeler için doğrulama ekleyin.
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
ms.openlocfilehash: e11f02aa17faffcfcd138136646c4a237bd697ec6cf9ff51797aaaaa63968bc2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264447"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Nasıl yapılır: Varlık sınıflarına doğrulama ekleme
Varlık sınıflarını *doğrulamak* , veri nesnelerine girilen değerlerin bir nesnenin şemasındaki kısıtlamalara ve ayrıca uygulama için belirlenen kurallara uygun olduğunu onaylama işlemidir. Temel alınan veritabanına güncelleştirmeleri göndermeden önce verilerin doğrulanması, hataları azaltan iyi bir uygulamadır. Ayrıca, bir uygulama ve veritabanı arasındaki gidiş dönüşlerin olası sayısını azaltır.

[Visual Studio LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , kullanıcıların, tüm varlıkların ekleme, güncelleştirme ve silme sırasında çalışan tasarımcı tarafından oluşturulan kodu genişletmelerine olanak tanıyan kısmi yöntemler sağlar ve ayrıca tek tek sütun değişiklikleri sırasında ve sonrasında.

> [!NOTE]
> Bu konuda, **O/R Tasarımcısı** kullanılarak varlık sınıflarına doğrulama eklemek için temel adımlar sağlanmaktadır. Belirli bir varlık sınıfına başvurulmadan bu genel adımların izlenmesi zor olabileceğinden, gerçek verileri kullanan bir anlatım sağlanır.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Belirli bir sütundaki değere yapılan değişiklikler için doğrulama ekleme
Bu yordam, bir sütundaki değer değiştiğinde verilerin nasıl doğrulandığını gösterir. Doğrulama, sınıf tanımı içinde (Kullanıcı arabirimi yerine) gerçekleştirildiğinden, değer doğrulamanın başarısız olmasına neden olursa bir özel durum oluşturulur. Uygulamanızda sütun değerlerini değiştirmeye çalışır olan kod için hata işlemeyi uygulayın.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Bir sütunun değer değişikliği sırasında verileri doğrulamak için

1. **O/R tasarımcısında** yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** **. dbml** dosyasına çift tıklayın.)

2. **O/R tasarımcısında**, doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi seçili varlık sınıfı için kısmi bir sınıf ile açılır.

3. İmleci kısmi sınıfa yerleştirin.

4. Visual Basic projeleri için:

    1. **Yöntem adı** listesini genişletin.

    2. Doğrulama eklemek istediğiniz sütun için **OnCOLUMNNAMEChanging** metodunu bulun.

    3. `OnCOLUMNNAMEChanging`Kısmi sınıfa bir yöntem eklenir.

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

    C# projeleri otomatik olarak olay işleyicileri oluşturmadığından, sütun değiştiren kısmi Yöntemler oluşturmak için IntelliSense 'i kullanabilirsiniz. `partial`Kullanılabilir kısmi yöntemlerin listesine erişmek için bir boşluk yazın. Doğrulama eklemek istediğiniz sütun için sütun değiştirme yöntemine tıklayın. Aşağıdaki kod, bir sütun değiştirme kısmi yöntemi seçtiğinizde oluşturulan koda benzer:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Bir varlık sınıfına güncelleştirmeler için doğrulama ekleme
Değişiklikler sırasında değerleri denetlemenin yanı sıra, bir bütün varlık sınıfını güncelleştirmek için bir deneme yapıldığında verileri de doğrulayabilirsiniz. Denenen bir güncelleştirme sırasında doğrulama, iş kuralları için gerekliyse, birden fazla sütundaki değerleri karşılaştırmanıza olanak sağlar. Aşağıdaki yordamda, bir bütün varlık sınıfını güncelleştirmek için bir girişim yapıldığında nasıl doğrulanacağı gösterilmektedir.

> [!NOTE]
> Varlık sınıflarının tamamlanma güncelleştirmeleri için doğrulama kodu, kısmi <xref:System.Data.Linq.DataContext> sınıfta yürütülür (belirli bir varlık sınıfının parçalı sınıfında yerine).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Bir varlık sınıfına yönelik bir güncelleştirme sırasında verileri doğrulamak için

1. **O/R tasarımcısında** yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** **. dbml** dosyasına çift tıklayın.)

2. **O/R tasarımcısında** boş bir alana sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi, için kısmi bir sınıf ile açılır `DataContext` .

3. İmleci için kısmi sınıfa yerleştirin `DataContext` .

4. Visual Basic projeleri için:

    1. **Yöntem adı** listesini genişletin.

    2. **Updateentityclassname** öğesine tıklayın.

    3. `UpdateENTITYCLASSNAME`Kısmi sınıfa bir yöntem eklenir.

    4. `instance`Aşağıdaki kodda gösterildiği gibi bağımsız değişkenini kullanarak ayrı sütun değerlerine erişin:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    C# projeleri için:

    C# projeleri otomatik olarak olay işleyicileri oluşturmadığından, kısmi yöntemi oluşturmak için IntelliSense 'i kullanabilirsiniz `UpdateCLASSNAME` . `partial`Kullanılabilir kısmi yöntemlerin listesine erişmek için bir boşluk yazın. Doğrulama eklemek istediğiniz sınıf için Update metoduna tıklayın. Aşağıdaki kod, kısmi bir yöntemi seçtiğinizde oluşturulan koda benzer `UpdateCLASSNAME` :

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

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Veriler doğrulanıyor](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
