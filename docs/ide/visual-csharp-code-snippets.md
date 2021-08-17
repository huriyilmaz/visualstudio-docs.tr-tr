---
title: C# kod parçacıkları
description: C# kod dosyalarınıza yaygın olarak kullanılan kod eklemek için kod parçacıklarını kullanmayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 8d6fef099eb827f2d618a91642fc88316611edf874bff14a2dae5a6cb27610f2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121399099"
---
# <a name="c-code-snippets"></a>C# kod parçacıkları

Kod parçacıkları, kodunuza hızla ekleyebilirsiniz hazır kod parçacıklarıdır. Örneğin, kod `for` parçacığı boş bir döngü `for` oluşturur. Bazı kod parçacıkları, kod satırlarını seçmenize ve ardından seçilen kod satırlarını içeren bir kod parçacığı seçmenize olanak sağlayan kod parçacıklarıyla çevreler. Örneğin, kod satırlarını seçerek kod parçacığını etkinleştirerek döngü bloğunda bu kod satırlarının yer alan `for` `for` bir döngü oluşturur. Kod parçacıkları program kodu yazmayı daha hızlı, daha kolay ve daha güvenilir hale getirir.

İmleç konuma bir kod parçacığı ekleyebilirsiniz veya seçili olan kodun çevresini çevreleyen kod parçacığını ekleyebilirsiniz. Kod Parçacığı Ekleme, **IntelliSense** menüsündeki Kod Parçacığı Ekle veya Surround **With** komutları aracılığıyla  veya **sırasıyla Ctrl** K , X veya Ctrl K , S klavye kısayolları kullanılarak +   + çağrılır.

Kod **Parçacığı Ekleyici,** tüm kullanılabilir kod parçacıkları için kod parçacığı adını görüntüler. Kod Parçacığı Ekleyici, kod parçacığının adını veya kod parçacığı adının bir kısmını yazarak bir giriş iletişim kutusu da içerir. Kod Parçacığı Ekleyici, bir kod parçacığı adıyla en yakın eşleşmeyi vurgular. Sekme **tuşuna** herhangi bir zamanda basılarak Kod Parçacığı Ekleyici'yi devreden çıkar ve seçili kod parçacığını ekler. Esc **tuşuna** basmak veya kod düzenleyicisinde fareye tıklamak, kod parçacığı eklemeden Kod Parçacığı Ekleyici'yi reddeder.

## <a name="default-code-snippets"></a>Varsayılan kod parçacıkları

Varsayılan olarak aşağıdaki kod parçacıkları C# Visual Studio dahil edilir.

|Ad (veya kısayol)|Açıklama|Kod parçacığı eklemek için geçerli konumlar|
| - |-----------------| - |
|#if|Bir [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) yönergesi ve bir [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) oluşturur.|Hiçbir yere.|
|#region|Bir [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) yönergesi ve bir [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) yönergesi oluşturur.|Hiçbir yere.|
|~|[İçeren sınıf](/dotnet/csharp/programming-guide/classes-and-structs/destructors) için bir sonlandırıcı (yıkıcı) oluşturur.|Bir sınıfın içinde.|
|özniteliği|sınıfından türeten bir sınıf için bildirim <xref:System.Attribute> oluşturur.|Bir ad alanının içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|checked|Denetlenen [bir blok](/dotnet/csharp/language-reference/keywords/checked) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|sınıf|Bir sınıf bildirimi oluşturur.|Bir ad alanının içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|ctor|İçeren sınıf için bir oluşturucu oluşturur.|Bir sınıfın içinde.|
|Cw|için bir çağrı <xref:System.Console.WriteLine%2A> oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|do|Bir do [döngüsü](/dotnet/csharp/language-reference/keywords/do) `while` oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|else|Başka bir [blok](/dotnet/csharp/language-reference/keywords/if-else) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|enum|Bir [enum bildirimi](/dotnet/csharp/language-reference/keywords/enum) oluşturur.|Bir ad alanının içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|equals|sınıfında tanımlanan yöntemi geçersiz kılmak için <xref:System.Object.Equals%2A> bir yöntem bildirimi <xref:System.Object> oluşturur.|Bir sınıfın veya yapının içinde.|
|Özel durum|Bir özel durumdan türeten bir sınıf için bildirim oluşturur ( <xref:System.Exception> varsayılan olarak).|Bir ad alanının içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|:|For [döngüsü](/dotnet/csharp/language-reference/keywords/for) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|foreach|[Foreach döngüsü](/dotnet/csharp/language-reference/keywords/foreach-in) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|forr|Her [yinelemeden](/dotnet/csharp/language-reference/keywords/for) sonra döngü değişkenlerini azalan bir for döngüsü oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|if|If [bloğu](/dotnet/csharp/language-reference/keywords/if-else) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|Dizinleyici|Dizin oluşturma bildirimi oluşturur.|Bir sınıfın veya yapının içinde.|
|arabirim|Arabirim [bildirimi](/dotnet/csharp/language-reference/keywords/interface) oluşturur.|Bir ad alanının içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|Çağırmak|Bir olayı güvenli bir şekilde çağıran bir blok oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|iterator|Bir bir birerator oluşturur.|Bir sınıfın veya yapının içinde.|
|iterindex|İç içe geçmiş bir sınıf kullanarak "adlandırılmış" bir iterator ve dizinleyici çifti oluşturur.|Bir sınıfın veya yapının içinde.|
|lock|Kilit [bloğu](/dotnet/csharp/language-reference/keywords/lock-statement) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|Mbox|için bir çağrı <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> oluşturur. için bir başvuru eklemeniz *System.Windows.Forms.dll.*|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|ad alanı|Bir ad [alanı bildirimi](/dotnet/csharp/language-reference/keywords/namespace) oluşturur.|Bir ad alanının içinde (genel ad alanı dahil).|
|Pervane|Otomatik [uygulanan bir özellik bildirimi](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) oluşturur.|Bir sınıfın veya yapının içinde.|
|propfull|ve erişimcileriyle bir `get` özellik `set` bildirimi oluşturur.|Bir sınıfın veya yapının içinde.|
|propg|Özel erişimci ile [salt okunur otomatik uygulanan](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) bir özellik `set` oluşturur.|Bir sınıfın veya yapının içinde.|
|Sım|Statik [bir](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) Main yöntem bildirimi oluşturur.|Bir sınıfın veya yapının içinde.|
|struct|Bir [yapı bildirimi](/dotnet/csharp/language-reference/keywords/struct) oluşturur.|Bir ad alanının içinde (genel ad alanı dahil), bir sınıf veya yapı.|
|Svm|Statik bir [void](/dotnet/csharp/language-reference/keywords/static) [Main](/dotnet/csharp/language-reference/keywords/void) yöntemi bildirimi oluşturur.|Bir sınıfın veya yapının içinde.|
|switch|Bir anahtar [bloğu](/dotnet/csharp/language-reference/keywords/switch) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|Deneme|Bir [try-catch bloğu](/dotnet/csharp/language-reference/keywords/try-catch) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|tryf|[Try-finally bloğu](/dotnet/csharp/language-reference/keywords/try-finally) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|unchecked|Denetlenmeyen [bir blok](/dotnet/csharp/language-reference/keywords/unchecked) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|unsafe|Güvenli olmayan [bir blok](/dotnet/csharp/language-reference/keywords/unsafe) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|
|kullanma|Bir using [yönergesi](/dotnet/csharp/language-reference/keywords/using-directive) oluşturur.|Bir ad alanının içinde (genel ad alanı dahil).|
|while|While [döngüsü](/dotnet/csharp/language-reference/keywords/while) oluşturur.|Bir yöntemin, dizinenin, özellik erişimcinin veya olay erişimcinin içinde.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacığı işlevleri](../ide/code-snippet-functions.md)
- [Kod parçacıkları](../ide/code-snippets.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Nasıl olur: Surround-with kod parçacıklarını kullanma](../ide/how-to-use-surround-with-code-snippets.md)
