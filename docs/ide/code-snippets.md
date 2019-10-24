---
title: Kod parçacıkları
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 09f6e2e9b4b89c7e6fd1fe9a342d4fd05b12e7a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747975"
---
# <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, sağ tıklama menüsü (bağlam menüsü) komutu veya kısayol tuşlarının birleşimini kullanarak bir kod dosyasına eklenebilen yeniden kullanılabilir kod bloklarında yer alabilir. Genellikle `try-finally` veya `if-else` blokları gibi yaygın olarak kullanılan kod blokları içerirler, ancak tüm sınıfları veya yöntemleri eklemek için kullanılabilirler.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets).

Kod parçacıkları,, Visual Basic, XML ve T-SQL dahil C#olmak C++üzere çok sayıda dilde kullanılabilir ve birkaç kez ad verebilir. Bir dile ait kullanılabilir tüm yüklü parçacıkları görüntülemek için, **Araçlar** menüsünden **kod parçacıkları Yöneticisi 'ni** açın (veya **ctrl** +**K**, **CTRL** +**B**) tuşlarına basın ve açılır menüden dili seçin en üstte.

![Kod parçacıkları Yöneticisi iletişim kutusu](media/code-snippets-manager.png)

Kod parçacıklarına aşağıdaki genel yollarla erişilebilir:

- Menü çubuğunda **düzenle**  > **IntelliSense** ' i seçin  > **kod parçacığı Ekle**

- Kod düzenleyicisindeki sağ tıklama veya bağlam menüsünde kod **parçacığı**  >  kod**parçacığı Ekle** ' yi seçin.

- Klavyeden **ctrl** +**K**,**CTRL** +**X** tuşlarına basın

## <a name="expansion-snippets-and-surround-with-snippets"></a>Genişleme parçacıkları ve surround-kod parçacıkları

Visual Studio 'da, belirtilen bir ekleme noktasına eklenen ve bir kod parçacığı kısayolunun yanı sıra (yalnızca ve yalnızca) kod parçacığı kısayolunu ve birlikte çevrelemeyi (C# yalnızca ve C++ yalnızca) içerebilen bir kod parçacığı olan iki tür kod parçacığı vardır.

Genişletme kod parçacığına bir örnek: C# tryf kısayolunun bir try-finally bloğu eklemek için kullanılır:

```csharp
try
{

}
finally
{

}
```

Kod penceresinin sağ tıklama menüsünde (bağlam menüsü) kod **parçacığı Ekle** ' **C#** ye tıklayıp, ardından `tryf` yazıp **Tab**tuşuna basarak bu kod parçacığını ekleyebilirsiniz. Ya da `tryf` yazabilir ve **Tab** tuşuna iki kez basabilirsiniz.

Kısayol `if` C++ , bir ekleme kod parçacığı ya da surround olarak kod parçacığı olarak kullanılabilir. Bir kod satırı seçerseniz (örneğin `return FALSE;`) ve sonra  >  **Ile çevrelemeyi** **seçerseniz, kod**parçacığı satır etrafında genişletilir:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Kod parçacığı değiştirme parametreleri

Kod parçacıkları, yazmakta olduğunuz kesin kodu sığdırmak için değiştirmeniz gereken yer tutucuları olan değiştirme parametrelerini içerebilir. Önceki örnekte `true`, uygun koşulla değiştireceğiniz bir değiştirme parametresidir. Yaptığınız değişiklik, kod parçacığında aynı değiştirme parametresinin her örneği için yinelenir.

Örneğin, Visual Basic bir özelliği ekleyen bir kod parçacığı vardır. Kod parçacığını eklemek için, Visual Basic kod dosyasındaki sağ tıklama veya bağlam menüsünden kod parçacığı**ekle** ** >  kod parçacığı öğesini** seçin. Ardından,**Özellikler, yordamlar, olaylar**  > **bir özellik tanımlamak** >  **kod düzenlerini** seçin.

![Özellik tanımlamak için kod parçacığı menüsü](media/code-snippets-vb-property.png)

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

@No__t_0 `m_property` olarak değiştirirseniz `newPropertyValue` her örneği değiştirilir. Özellik bildiriminde `Int` `String` değiştirirseniz, set yöntemindeki değer de `Int` olarak değiştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [Nasıl yapılır: kod parçacıklarını dağıtma](../ide/how-to-distribute-code-snippets.md)
- [Kod parçacıkları kullanmak için en iyi uygulamalar](../ide/best-practices-for-using-code-snippets.md)
- [Sorun giderme parçacıkları](../ide/troubleshooting-snippets.md)
- [C#kod parçacıkları](../ide/visual-csharp-code-snippets.md)
- [C++kod parçacıkları](../ide/visual-cpp-code-snippets.md)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
- [Kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets)
