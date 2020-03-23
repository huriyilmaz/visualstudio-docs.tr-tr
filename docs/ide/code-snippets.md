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
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585424"
---
# <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, sağ tıklatma menüsü (bağlam menüsü) komutu veya anahtarlıkların birleşimi kullanılarak kod dosyasına eklenebilen küçük yeniden kullanılabilir kod bloklarıdır. Genellikle, örneğin veya `try-finally` `if-else` bloklar gibi yaygın olarak kullanılan kod blokları içerir, ancak tüm sınıfları veya yöntemleri eklemek için kullanılabilir.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için [Kod parçacıklarına (Mac için Visual Studio)](/visualstudio/mac/snippets)bakın.

C#, C++, Visual Basic, XML ve T-SQL gibi çok sayıda dil için kod parçacıkları kullanılabilir. Bir dil için mevcut tüm yüklü parçacıkları görüntülemek için **Araçlar** menüsünden **Kod Parçacıkları Yöneticisi'ni** açın (veya **Ctrl**+**K**, **Ctrl**+**B**tuşuna basın), ve üstteki açılır menüden dili seçin.

![Kod Parçacıkları Yöneticisi iletişim kutusu](media/code-snippets-manager.png)

Kod parçacıklarına aşağıdaki genel yollarla erişilebilir:

- Menü çubuğunda**IntelliSense** > **Ekle Snippet'i** **Edit'i** > seçin

- Kod düzenleyicisindeki sağ tıklatma veya bağlam menüsünden **Snippet** > **Ekle Snippet'i** seçin

- Klavyeden **Ctrl**+**K**,**Ctrl**+**X** tuşlarına basın

## <a name="expansion-snippets-and-surround-with-snippets"></a>Genişletme parçacıkları ve surround-snippets ile

Visual Studio'da iki tür kod parçacığı vardır: belirli bir ekleme noktasına eklenen ve bir snippet kısayolu yerine dizilebilecek genişletme parçacıkları ve seçili bir kod bloğunun etrafına eklenen parçacıklarla (yalnızca C# ve C++) surround.

Genişletme parçacığı örneği: C#'da try-finally bloğunu eklemek için kısayol tryf kullanılır:

```csharp
try
{

}
finally
{

}
```

Bu snippet'i kod penceresinin sağ tıklama menüsüne (bağlam menüsü) **Ekle'yi** tıklatarak ekleyebilirsiniz, ardından `tryf` **Visual C#** yazın ve sonra **Sekme tuşuna**basabilirsiniz. Veya `tryf` **Sekme'yi** iki kez yazıp basabilirsiniz.

Surround ile snippet örneği: C++'da kısayol `if` ekleme snippeti veya surround-with snippet olarak kullanılabilir. Bir kod satırı `return FALSE;`seçerseniz (örneğin), ve sonra Surround **With'i** > **seçerseniz,** parçacık satır ın etrafında genişletilir:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Snippet değiştirme parametreleri

Parçacıklar, yazdığınız kesin kodu sığdırmak için değiştirmeniz gereken yer tutucular olan değiştirme parametreleri içerebilir. Önceki örnekte, `true` uygun koşulla değiştireceğiniz yedek bir parametre yer alır. Yaptığınız değiştirme, parçacıktaki aynı değiştirme parametresinin her örneği için yinelenir.

Örneğin, Visual Basic'te bir özellik ekleyen bir kod parçacığı vardır. Parçacık eklemek için Visual Basic kod dosyasındaki sağ tıklatma veya bağlam menüsünden **Snippet** > **Ekle Snippet'i** seçin. Daha sonra, **Kod Desenleri** > **Özellikleri, Yordamlar, Olaylar** > **Bir Özellik tanımlayın**seçin.

![Özellik Tanımla için kod snippet menüsü](media/code-snippets-vb-property.png)

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

Değiştirirseniz, `newPropertyValue` her örneği `newPropertyValue` değiştirilir. `m_property` Özellik `String` `Int` bildiriminde değiştirilirseniz, ayarlanan yöntemdeki değer de `Int`.

## <a name="see-also"></a>Ayrıca bkz.

- [Walkthrough: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [Nasıl yapılır: Kod parçacıklarını dağıtma](../ide/how-to-distribute-code-snippets.md)
- [Kod parçacıklarını kullanmak için en iyi uygulamalar](../ide/best-practices-for-using-code-snippets.md)
- [Sorun giderme parçacıkları](../ide/troubleshooting-snippets.md)
- [C# kod parçacıkları](../ide/visual-csharp-code-snippets.md)
- [C++ kod parçacıkları](../ide/visual-cpp-code-snippets.md)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
- [Kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets)
