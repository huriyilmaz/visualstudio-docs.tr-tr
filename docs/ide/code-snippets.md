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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585424"
---
# <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, sağ tıklama menüsü (bağlam menüsü) komutu veya kısayol tuşlarının birleşimini kullanarak bir kod dosyasına eklenebilen yeniden kullanılabilir kod bloklarında yer alabilir. Genellikle, veya blokları gibi yaygın olarak kullanılan kod blokları içerirler `try-finally` `if-else` , ancak tüm sınıfları veya yöntemleri eklemek için kullanılabilirler.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets).

Kod parçacıkları, C#, C++, Visual Basic, XML ve T-SQL dahil olmak üzere çok sayıda dilde kullanılabilir ve birkaç kez ad verebilir. Bir dile ait kullanılabilir tüm yüklü parçacıkları görüntülemek için, **Araçlar** menüsünden **kod parçacıkları Yöneticisi 'ni** açın (veya **CTRL** + **K**, **CTRL** + **B**tuşlarına basın) ve en üstteki açılan menüden dili seçin.

![Kod parçacıkları Yöneticisi iletişim kutusu](media/code-snippets-manager.png)

Kod parçacıklarına aşağıdaki genel yollarla erişilebilir:

- Menü çubuğunda, IntelliSense **Düzenle**  >  **IntelliSense**  >  **kod parçacığı Ekle** ' yi seçin.

- Kod düzenleyicisindeki sağ tıklama veya bağlam menüsünde kod **parçacığı**  >  **ekleme kod parçacığı** ' ni seçin.

- Klavyeden **CTRL** + **K**,**CTRL** + **X** tuşlarına basın

## <a name="expansion-snippets-and-surround-with-snippets"></a>Genişleme parçacıkları ve surround-kod parçacıkları

Visual Studio 'da, belirtilen bir ekleme noktasına eklenen ve kod parçacığı kısayolunun yanı sıra bir kod parçacığı kısayolunun (yalnızca C# ve C++) yerini alacak şekilde iki tür kod parçacığı vardır: genişletme parçacıkları.

Bir genişletme kod parçacığına örnek: C# ' de, try-finally bloğu eklemek için tryf kısayolu kullanılır:

```csharp
try
{

}
finally
{

}
```

Kod penceresinin sağ tıklama menüsünde (bağlam menüsü) kod **parçacığı Ekle** ' ye tıklayıp, ardından **Visual C#**, sonra yazarak `tryf` ve ardından **sekme**tuşuna basarak bu parçacığı ekleyebilirsiniz. İsterseniz `tryf` **Tab** tuşuna iki kez yazabilir ve basabilirsiniz.

Bir surround-kod parçacığı ile bir örnek: C++ ' da, `if` ekleme parçacığı ya da bir surround olarak kod parçacığı olarak kullanılabilir. Bir kod satırı seçer (örneğin `return FALSE;` ) ve ardından **birlikte Çevrele**seçeneğini belirlerseniz, kod  >  **if**parçacığı satır etrafında genişletilir:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Kod parçacığı değiştirme parametreleri

Kod parçacıkları, yazmakta olduğunuz kesin kodu sığdırmak için değiştirmeniz gereken yer tutucuları olan değiştirme parametrelerini içerebilir. Önceki örnekte `true` , uygun koşulla değiştireceğiniz bir değiştirme parametresidir. Yaptığınız değişiklik, kod parçacığında aynı değiştirme parametresinin her örneği için yinelenir.

Örneğin, Visual Basic bir özelliği ekleyen bir kod parçacığı vardır. Kod parçacığını eklemek için, **Snippet**  >  bir Visual Basic kod dosyasındaki sağ tıklama veya bağlam menüsünden kod parçacığı**Ekle kod parçacığını** seçin. Ardından, **kod desenleri**  >  **özelliklerini, yordamları, olayları**  >  **bir özelliği tanımlar**.

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

`newPropertyValue`' A geçiş yaparsanız `m_property` , her örneği `newPropertyValue` değiştirilir. `String` `Int` Özelliğini özellik bildiriminde olarak değiştirirseniz, set yöntemindeki değer de olarak değiştirilir `Int` .

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [Nasıl yapılır: kod parçacıklarını dağıtma](../ide/how-to-distribute-code-snippets.md)
- [Kod parçacıkları kullanmak için en iyi uygulamalar](../ide/best-practices-for-using-code-snippets.md)
- [Sorun giderme parçacıkları](../ide/troubleshooting-snippets.md)
- [C# kod parçacıkları](../ide/visual-csharp-code-snippets.md)
- [C++ kod parçacıkları](../ide/visual-cpp-code-snippets.md)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
- [Kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets)
