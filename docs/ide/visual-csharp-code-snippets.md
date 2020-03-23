---
title: C# kod parçacıkları
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d41907a15b7e0b1692dda3f4d678c2b843dfcd03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594168"
---
# <a name="c-code-snippets"></a>C# kod parçacıkları

Kod parçacıkları, kodunuza hızlı bir şekilde ekebileceğiniz hazır kod parçacıklarıdır. Örneğin, `for` kod snippet boş `for` bir döngü oluşturur. Bazı kod parçacıkları, kod satırlarını seçmenize ve ardından seçilen kod satırlarını içeren bir kod parçacığı seçmenize olanak tanıyan kod parçacıklarıyla çevrelenir. Örneğin, kod satırlarını seçip `for` kod parçacıklarını etkinleştirdiğinizde, döngü bloğunun içinde bu kod satırlarıyla bir `for` döngü oluşturur. Kod parçacıkları program kodu yazmayı daha hızlı, daha kolay ve daha güvenilir hale getirebilir.

İmleç konumuna bir kod parçacığı ekleyebilir veya şu anda seçili kodun etrafına bir surround kod parçacığı ekleyebilirsiniz. Kod Snippet Kesici, **IntelliSense** menüsündeki komutlarla **Insert Kodu Snippet** veya **Surround** komutları aracılığıyla veya sırasıyla Klavye kısayolları **Ctrl**+**K**,**X** veya **Ctrl**+**K**,**S** kullanılarak çağrılır.

**Code Snippet Inserter,** kullanılabilir tüm kod parçacıkları için kod snippet adını görüntüler. Kod Snippet Inserter ayrıca kod snippet adını veya kod snippet adının bir kısmını yazabilirsiniz bir giriş iletişim kutusu içerir. Kod Snippet Inserter, kod parçacığı adına en yakın eşleşmeyi vurgular. **Sekme** tuşuna herhangi bir zamanda basıldığında Kod Snippet Inserter'i kapatAcak ve şu anda seçili kod snippet'ini ekler. **Esc** tuşuna basmak veya kod düzenleyicisindeki fareyi tıklatmak, kod snippet'i eklemeden Kod Kesici'yi görevden alacaktır.

## <a name="default-code-snippets"></a>Varsayılan kod parçacıkları

Varsayılan olarak aşağıdaki kod parçacıkları C# için Visual Studio'ya dahildir.

|Ad (veya kısayol)|Açıklama|Parçacık eklemek için geçerli konumlar|
| - |-----------------| - |
|#if|[bir #if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) yönergesi ve [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) yönergesi oluşturur.|Hiçbir yere.|
|#region|[bir #region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) yönergesi ve [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) yönergesi oluşturur.|Hiçbir yere.|
|~|İçeren sınıf için bir [sonlandırıcı](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (yıkıcı) oluşturur.|Bir sınıfın içinde.|
|özniteliği|'den <xref:System.Attribute>türeyen bir sınıf için bir bildirim oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya bir yapı içinde.|
|checked|[Denetlenmiş](/dotnet/csharp/language-reference/keywords/checked) bir blok oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|sınıf|Bir sınıf bildirimi oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya bir yapı içinde.|
|ctor|İçerme sınıfı için bir oluşturucu oluşturur.|Bir sınıfın içinde.|
|Cw|'ye <xref:System.Console.WriteLine%2A>çağrı oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|do|[Bir do](/dotnet/csharp/language-reference/keywords/do) `while` döngüsü oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|else|[Başka](/dotnet/csharp/language-reference/keywords/if-else) bir blok oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|enum|[Bir enum](/dotnet/csharp/language-reference/keywords/enum) bildirimi oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya bir yapı içinde.|
|equals|<xref:System.Object> Sınıfta tanımlanan <xref:System.Object.Equals%2A> yöntemi geçersiz kılan bir yöntem bildirimi oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|Özel durum|Bir özel durum (varsayılan<xref:System.Exception> olarak) türetilen bir sınıf için bir bildirim oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya bir yapı içinde.|
|for|[For](/dotnet/csharp/language-reference/keywords/for) döngüsü oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|foreach|[Foreach](/dotnet/csharp/language-reference/keywords/foreach-in) döngüsü oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|forr|Her yinelemeden sonra döngü değişkenini veren bir [for](/dotnet/csharp/language-reference/keywords/for) döngüsü oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|if|[If](/dotnet/csharp/language-reference/keywords/if-else) bloğu oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|Dizinleyici|Dizin leyici bildirimi oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|arabirim|[Arabirim](/dotnet/csharp/language-reference/keywords/interface) bildirimi oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya bir yapı içinde.|
|Çağırmak|Bir olayı güvenli bir şekilde çağıran bir blok oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|iterator|Bir yineleyici oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|iterindex|İç içe bir sınıf kullanarak "adlandırılmış" yineleyici ve dizinleyici çifti oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|lock|Bir [kilit](/dotnet/csharp/language-reference/keywords/lock-statement) bloğu oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|Mbox|'ye <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>çağrı oluşturur. *System.Windows.Forms.dll*adresine bir başvuru eklemeniz gerekebilir.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|ad alanı|[Ad alanı](/dotnet/csharp/language-reference/keywords/namespace) bildirimi oluşturur.|Ad alanı içinde (genel ad alanı dahil).|
|Pervane|[Otomatik olarak uygulanan bir özellik](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) bildirimi oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|propfull|Bir özellik bildirimi `get` ve `set` erişimci oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|propg|Özel `set` bir erişimciyle salt okunur [otomatik olarak uygulanan](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) bir özellik oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|Sım|[Statik](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) Main yöntem bildirimi oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|struct |Bir [yapı](/dotnet/csharp/language-reference/keywords/struct) bildirimi oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya bir yapı içinde.|
|Svm|[Statik](/dotnet/csharp/language-reference/keywords/static) bir [boşluk](/dotnet/csharp/language-reference/keywords/void) Ana yöntem bildirimi oluşturur.|Bir sınıfın ya da bir yapının içinde.|
|switch|Bir [anahtar](/dotnet/csharp/language-reference/keywords/switch) bloğu oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|Deneme|[Try-catch](/dotnet/csharp/language-reference/keywords/try-catch) bloğu oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|tryf|[Bir try-finally](/dotnet/csharp/language-reference/keywords/try-finally) blok oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|unchecked|[Denetlenmemiş](/dotnet/csharp/language-reference/keywords/unchecked) bir blok oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|unsafe|[Güvenli olmayan](/dotnet/csharp/language-reference/keywords/unsafe) bir blok oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|
|kullanma|[Bir kullanma](/dotnet/csharp/language-reference/keywords/using-directive) yönergesi oluşturur.|Ad alanı içinde (genel ad alanı dahil).|
|while|Bir [while](/dotnet/csharp/language-reference/keywords/while) döngüsü oluşturur.|Bir yöntemin içinde, bir dizinleyici, özellik erişimcisi veya olay erişimcisi.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacığı işlevleri](../ide/code-snippet-functions.md)
- [Kod parçacıkları](../ide/code-snippets.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Nasıl kullanılır: Surround kod parçacıkları kullanın](../ide/how-to-use-surround-with-code-snippets.md)
