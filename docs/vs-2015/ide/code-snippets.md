---
title: Kod parçacıkları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b41b6e4d4a7635b32edb5697c89ecb1249fb9da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619723"
---
# <a name="code-snippets"></a>Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacıkları, bağlam menüsü komutu veya kısayol tuşlarının birleşimini kullanarak bir kod dosyasına eklenebilen yeniden kullanılabilir kod bloklarında yer alabilir. Genellikle try-finally veya if-else blokları gibi yaygın olarak kullanılan kod blokları içerirler, ancak tüm sınıfları veya yöntemleri eklemek için kullanılabilirler.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Genişleme parçacıkları ve surround-kod parçacıkları
 Visual Studio 'da, belirtilen bir ekleme noktasına eklenen ve bir kod parçacığı kısayolunun yanı sıra (yalnızca ve yalnızca) kod parçacığı kısayolunu ve birlikte çevrelemeyi (C# yalnızca ve C++ yalnızca) içerebilen bir kod parçacığı olan iki tür kod parçacığı vardır.

 Bir ekleme kod parçacığına bir örnek: C# tryf kısayolunun bir try-finally bloğu eklemek için kullanılır:

```
try
{

}
finally
{

}

```

 Kod penceresinin bağlam menüsünde kod **parçacığı Ekle** ' ye tıklayıp ardından **görsel C#** ' i yazıp `tryf`, sonra sekme yazıp `tryf` yazıp sekme + SEKME tuşlarına basarak bu parçacığı ekleyebilirsiniz.

 Kısayol `if` C++ , bir ekleme kod parçacığı ya da surround olarak kod parçacığı olarak kullanılabilir. Bir kod satırı seçerseniz (örneğin `return FALSE;`) **ve ardından** **ile Çevrele**' ye tıklarsanız, kod parçacığı satır etrafında genişletilir:

```
if (true)
{
    return FALSE;
}

```

## <a name="snippet-replacement-parameters"></a>Kod parçacığı değiştirme parametreleri
 Kod parçacıkları, yazmakta olduğunuz kesin kodu sığdırmak için değiştirmeniz gereken yer tutucuları olan değiştirme parametrelerini içerebilir. Önceki örnekte `true`, uygun koşulla değiştireceğiniz bir değiştirme parametresidir. Yaptığınız değişiklik, kod parçacığında aynı değiştirme parametresinin her örneği için yinelenir.

 Örneğin, Visual Basic bir özelliği ekleyen bir kod parçacığı vardır. Kod penceresinin bağlam menüsünde **parçacığı Ekle** ' ye tıklayın, ardından **kod desenleri**, **Özellikler, yordamlar, olaylar**ve bir özellik tanımlayın. Aşağıdaki kod eklenir:

```
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

## <a name="code-snippet-manager"></a>Kod parçacığı Yöneticisi
 **Araçlar/kod parçacıkları Yöneticisi**' ne tıklayarak şu anda yüklü olan tüm kod parçacıklarını ve disk üzerindeki konumlarını görebilirsiniz. Kod parçacıkları dile göre görüntülenir.

 **Kod parçacıkları Yöneticisi** Iletişim kutusunda **ekleme** ve **kaldırma** düğmeleri ile kod parçacığı dizinleri ekleyebilir ve kaldırabilirsiniz. Bağımsız kod parçacıkları eklemek için **Içeri aktar** düğmesini kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md) [nasıl yapılır:](../ide/how-to-distribute-code-snippets.md) kod parçacıkları [Ile ilgili en iyi yöntemleri](../ide/best-practices-for-using-code-snippets.md) dağıtma kod parçacıkları [sorun giderme parçacıkları](../ide/troubleshooting-snippets.md) [görsel C# kod parçacıkları](../ide/visual-csharp-code-snippets.md) [görsel C++ kod parçacıkları](../ide/visual-cpp-code-snippets.md) [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
