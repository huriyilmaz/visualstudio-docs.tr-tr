---
title: Kod parçacıkları
description: Kod parçacıkları ve bunların bir kod dosyasına eklenebilir küçük yeniden kullanılabilir kod blokları olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: feb6da780d14404599254e6dafc021e3ce4e431f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056348"
---
# <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, sağ tıklama menüsü (bağlam menüsü) komutu veya kısayol tuşları birleşimi kullanılarak kod dosyasına eklenebilir, yeniden kullanılabilir küçük kod bloklarıdır. Bunlar genellikle veya blokları gibi yaygın olarak kullanılan kod bloklarını içerir, ancak sınıfların veya `try-finally` `if-else` yöntemlerin tamamını eklemek için kullanılabilir.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets).

Kod parçacıkları C#, C++, Visual Basic, XML ve T-SQL gibi birçok dilde kullanılabilir. Bir dil için kullanılabilen tüm yüklü kod parçacıklarını görüntülemek için  Araçlar menüsünden Kod Parçacıkları **Yöneticisi'ni** açın (veya **Ctrl** + **K**, **Ctrl** B tuşlarına basın) ve üst açılan menüden dili + seçin.

![Kod Parçacıkları Yöneticisi iletişim kutusu](media/code-snippets-manager.png)

Kod parçacıklarına aşağıdaki genel yollarla erişilebilir:

- Menü çubuğunda   >  **IntelliSense Ekleme Parçacığını Düzenle'yi**  >  **seçin**

- Kod düzenleyicisinde sağ tıklama veya bağlam menüsünde Kod Parçacığı Ekleme Kod **Parçacığı'yı**  >  **seçin**

- Klavyeden **Ctrl** + **K**,**Ctrl** X + **tuşlarına basın**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Genişletme kod parçacıkları ve çevreli kod parçacıkları

Bu Visual Studio iki tür kod parçacığı vardır: belirtilen ekleme noktasına eklenen ve bir kod parçacığı kısayolunu değiştiren genişletme kod parçacıkları ve seçili bir kod bloğu çevresinde eklenen kod parçacıkları (yalnızca C# ve C++ ).

Genişletme kod parçacığı örneği: C# içinde tryf kısayolu bir try-finally bloğu eklemek için kullanılır:

```csharp
try
{

}
finally
{

}
```

Kod penceresinin sağ  tıklama menüsünde (bağlam menüsü) Kod Parçacığı Ekle'ye ve **ardından Visual C#** tuşuna ve ardından Sekme tuşuna basarak bu kod `tryf` parçacığını **ekleyebilirsiniz.** Veya Sekme tuşuna iki `tryf` kez basabilirsiniz. 

Surround-with kod parçacığına örnek: C++ içinde kısayol ekleme kod parçacığı olarak veya `if` surround-with kod parçacığı olarak kullanılabilir. Bir kod satırı seçerseniz (örneğin) ve ardından Varsa Ile Çevrele'yi `return FALSE;`   >  **seçerseniz** kod parçacığı satırın çevresinde genişletilir:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Kod parçacığı değiştirme parametreleri

Kod parçacıklarında, yazmakta olan kodu tam olarak sığdırmak için değiştirmeniz gereken yer tutucular olan değiştirme parametreleri olabilir. Önceki örnekte, `true` uygun koşulla değiştire bir değiştirme parametresi vardır. Kod parçacığında aynı değiştirme parametresinin her örneği için sizin değişikliğinizi tekrarlar.

Örneğin, Visual Basic özelliği ekli bir kod parçacığı vardır. Kod parçacığını eklemek için bir **kod dosyasındaki** sağ tıklama veya bağlam menüsünden  >   Kod Parçacığı Ekleme Visual Basic seçin. Ardından Kod Desenleri **Özellikleri, Yordamlar,**  >  **Olaylar Bir Özellik**  >  **Tanımlayın'ı seçin.**

![Özellik Tanımlama için kod parçacığı menüsü](media/code-snippets-vb-property.png)

Aşağıdaki kod eklenir:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

olarak `newPropertyValue` `m_property` değiştirirsanız, her örneği `newPropertyValue` değiştirilir. özellik `String` bildiriminde `Int` değerini olarak değiştirirsanız, set yönteminde değeri de olarak `Int` değiştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [Nasıl: Kod parçacıklarını dağıtma](../ide/how-to-distribute-code-snippets.md)
- [Kod parçacıklarını kullanmaya yönelik en iyi yöntemler](../ide/best-practices-for-using-code-snippets.md)
- [Kod parçacıklarıyla ilgili sorunları giderme](../ide/troubleshooting-snippets.md)
- [C# kod parçacıkları](../ide/visual-csharp-code-snippets.md)
- [C++ kod parçacıkları](../ide/visual-cpp-code-snippets.md)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
- [Kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets)
