---
title: C# kod parçacıkları
description: C# kod dosyalarınıza yaygın olarak kullanılan kodu eklemek için kod parçacıklarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 46b2d231f1fa9a0e90538c426f48c86e5fafecbe
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478763"
---
# <a name="c-code-snippets"></a>C# kod parçacıkları

Kod parçacıkları, kodunuza hızlı bir şekilde ekleyebileceğiniz kod parçacıklarında kullanıma sunulur. Örneğin, `for` kod parçacığı boş bir `for` döngü oluşturur. Bazı kod parçacıkları, kod satırları seçmenize olanak tanıyan kod parçacıkları ile çevredir ve seçilen kod satırlarını içeren bir kod parçacığı seçer. Örneğin, kod satırları ' nı seçip `for` kod parçacığını etkinleştirdikten sonra, `for` Bu kod satırlarıyla döngü bloğu içinde bir döngü oluşturur. Kod parçacıkları program kodunu daha hızlı, daha kolay ve daha güvenilir bir şekilde yazmayı kolaylaştırabilir.

İmleç konumuna bir kod parçacığı ekleyebilir veya şu anda seçili olan kodun çevresine bir surround kod parçacığı ekleyebilirsiniz. Kod parçacığı **ekleme kodu kod parçacığı Ekle** veya **IntelliSense** menüsündeki komutlarla **Çevrele** veya sırasıyla **CTRL** + **k**,**X** ya da **CTRL** + **k****, klavye** kısayolları kullanılarak çağrılır.

**Kod parçacığı Inserter** , tüm kullanılabilir kod parçacıkları için kod parçacığı adını görüntüler. Kod parçacığı Inserter, kod parçacığının adını veya kod parçacığı adının bir bölümünü girebileceğiniz bir giriş iletişim kutusu da içerir. Kod parçacığı Inserter, bir kod parçacığı adına en yakın eşleşmeyi vurgular. İstediğiniz zaman **Tab** tuşuna basıldığında kod parçacığı eklenebilir ve şu anda seçili kod parçacığı işaretlenir. Kod Düzenleyicisi 'nde **ESC** tuşuna basmak veya fareye tıklamak, kod parçacığı eklemeden kod parçacığı ınsertıkesini kapatabilir.

## <a name="default-code-snippets"></a>Varsayılan kod parçacıkları

Varsayılan olarak, aşağıdaki kod parçacıkları C# için Visual Studio 'Ya eklenmiştir.

|Ad (veya kısayol)|Açıklama|Kod parçacığı eklemek için geçerli konumlar|
| - |-----------------| - |
|#if|Bir [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) yönergesi ve [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) yönergesi oluşturur.|Yerdeki.|
|#region|Bir [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) yönergesi ve [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) yönergesi oluşturur.|Yerdeki.|
|~|İçerilen sınıf için bir [Sonlandırıcı](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (yıkıcı) oluşturur.|Bir sınıf içinde.|
|özniteliği|Öğesinden türetilen bir sınıf için bir bildirim oluşturur <xref:System.Attribute> .|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|checked|[Denetlenen](/dotnet/csharp/language-reference/keywords/checked) bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|sınıf|Bir sınıf bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|'u|İçerilen sınıf için bir Oluşturucu oluşturur.|Bir sınıf içinde.|
|fiili|Öğesine bir çağrı oluşturur <xref:System.Console.WriteLine%2A> .|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|do|[Do](/dotnet/csharp/language-reference/keywords/do) `while` döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|else|[Else](/dotnet/csharp/language-reference/keywords/if-else) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|enum|Bir [sabit listesi](/dotnet/csharp/language-reference/keywords/enum) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|equals|Sınıfında tanımlanan yöntemi geçersiz kılan bir yöntem bildirimi oluşturur <xref:System.Object.Equals%2A> <xref:System.Object> .|Bir sınıf veya yapı içinde.|
|duruma|Özel durumdan türetilen bir sınıf için bir bildirim oluşturur ( <xref:System.Exception> Varsayılan olarak).|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|:|[For](/dotnet/csharp/language-reference/keywords/for) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|foreach|Bir [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|Öğrencilerinize|Her yinelemeden sonra döngü değişkenini azaltır bir [for](/dotnet/csharp/language-reference/keywords/for) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|if|[IF](/dotnet/csharp/language-reference/keywords/if-else) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|dizinleyic|Bir Dizin Oluşturucu bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|arabirim|[Arabirim](/dotnet/csharp/language-reference/keywords/interface) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|Resync|Güvenli bir şekilde olay çağıran bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|iterator|Bir yineleyici oluşturur.|Bir sınıf veya yapı içinde.|
|yinedizin|İç içe bir sınıf kullanarak "adlandırılmış" yineleyici ve Dizin Oluşturucu çifti oluşturur.|Bir sınıf veya yapı içinde.|
|lock|Bir [kilit](/dotnet/csharp/language-reference/keywords/lock-statement) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|MBOX|Öğesine bir çağrı oluşturur <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> . *System.Windows.Forms.dll* bir başvuru eklemeniz gerekebilir.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|ad alanı|Bir [ad alanı](/dotnet/csharp/language-reference/keywords/namespace) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil).|
|Prop|[Otomatik uygulanan bir özellik](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|propfull|Ve erişimcileri ile bir özellik bildirimi oluşturur `get` `set` .|Bir sınıf veya yapı içinde.|
|propg|Özel erişimcisi olan salt okunurdur bir [Otomatik uygulanmış özellik](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) oluşturur `set` .|Bir sınıf veya yapı içinde.|
|SIM|Statik bir [static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) Main yöntemi bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|struct|Bir [struct](/dotnet/csharp/language-reference/keywords/struct) bildirimi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|SVM|[Statik](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) Main yöntemi bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|switch|Bir [anahtar](/dotnet/csharp/language-reference/keywords/switch) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|Deneme|[Try-catch](/dotnet/csharp/language-reference/keywords/try-catch) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|tryf|[Try-finally](/dotnet/csharp/language-reference/keywords/try-finally) bloğu oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|unchecked|[Denetlenmemiş](/dotnet/csharp/language-reference/keywords/unchecked) bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|unsafe|[Güvenli olmayan](/dotnet/csharp/language-reference/keywords/unsafe) bir blok oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|
|kullanma|Bir [using](/dotnet/csharp/language-reference/keywords/using-directive) yönergesi oluşturur.|Bir ad alanı içinde (genel ad alanı dahil).|
|while|[While](/dotnet/csharp/language-reference/keywords/while) döngüsü oluşturur.|Bir yöntem içinde, bir Dizin Oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacığı işlevleri](../ide/code-snippet-functions.md)
- [Kod parçacıkları](../ide/code-snippets.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Nasıl yapılır: kod parçacıkları ile surround kullanma](../ide/how-to-use-surround-with-code-snippets.md)
