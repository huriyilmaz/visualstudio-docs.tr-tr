---
title: Dosyalar için derleme eylemleri
description: bir Visual Studio projesindeki tüm dosyaların yapı eylemine sahip olduğunu ve derleme eyleminin, proje derlendiğinde dosyaya ne olduğunu nasıl denetlediğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bb9678d421e9e12c3595806af1afcfe1f1fd82ad760aa3aaa3934149f59ff51
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234063"
---
# <a name="build-actions"></a>Derleme eylemleri

bir Visual Studio projesindeki tüm dosyaların bir yapı eylemi vardır. Yapı eylemi, proje derlendiğinde dosyaya ne olacağını denetler.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio içindeki derleme eylemleri](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Yapı eylemi ayarla

Bir dosyaya yönelik derleme eylemini ayarlamak için, **Çözüm Gezgini** dosya ' da bir dosyayı seçip **alt** ENTER ' a basarak **Özellikler** penceresinde dosyanın özelliklerini açın + . Ya da **Çözüm Gezgini** ' de dosyaya sağ tıklayıp **Özellikler**' i seçin. **Özellikler** penceresinde, **Gelişmiş** bölümünde, dosya için derleme eylemi ayarlamak için **Oluştur eylemi** ' nin yanındaki açılan listeyi kullanın.

![Visual Studio bir dosya için oluşturma eylemleri](media/build-actions.png)

## <a name="build-action-values"></a>Derleme eylemi değerleri

C# ve Visual Basic proje dosyaları için daha yaygın olarak kullanılan derleme eylemlerinden bazıları şunlardır:

|Derleme eylemi | Project türleri | Açıklama |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | C# veya Visual Basic derleyicisine giriş olarak geçirilen kaynak olmayan bir metin dosyası. Bu derleme eylemi, genellikle kod kalitesini doğrulamak üzere bir proje tarafından başvurulan [çözümleyiciler](../code-quality/roslyn-analyzers-overview.md) için giriş sağlamak üzere kullanılır. Daha fazla bilgi için bkz. [ek dosyaları kullanma](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **ApplicationDefinition** | WPF | Uygulamanızı tanımlayan dosya. İlk kez bir proje oluşturduğunuzda, bu *app. xaml*' dir. |
| **CodeAnalysisDictionary** | .NET | yazım denetimi için Code Analysis tarafından kullanılan özel bir sözcük sözlüğü. bkz [. nasıl yapılır: Code Analysis sözlüğünü özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Se** | herhangi biri | Dosya derleyiciye kaynak dosya olarak geçirilir.|
| **İçerik** | .NET | **İçerik** olarak işaretlenen bir dosya, çağırarak akış olarak alınabilir <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> . ASP.NET projeleri için, bu dosyalar dağıtıldığında sitenin bir parçası olarak dahil edilir.|
| **DesignData** | WPF | Kullanıcı denetimlerinin tasarım zamanında, kukla türler ve örnek verilerle görüntülenmesini sağlamak için XAML ViewModel dosyaları için kullanılır. |
| **DesignDataWithDesignTimeCreateable** | WPF | **Designdata** gibi, ancak gerçek türler.  |
| **Gömülü kaynak** | .NET | Dosya, derlemeye gömülebilen bir kaynak olarak derleyiciye geçirilir. <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName>Derlemeden dosyayı okumak için öğesini çağırabilirsiniz.|
| **EntityDeploy** | .NET | EF yapıtlarının dağıtımını belirten Entity Framework (EF). edmx dosyaları için. |
| **Fakes** | .NET | Microsoft Fakes test çerçevesi için kullanılır. Bkz. [Microsoft Fakes kullanarak test altında kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Hiçbiri** | herhangi biri | Dosya, herhangi bir şekilde derleme kapsamında değildir. Bu değer, örneğin "Benioku" dosyaları gibi belge dosyaları için kullanılabilir.|
| **Sayfa** | WPF | Çalışma zamanında daha hızlı yükleme yapmak için bir XAML dosyasını bir binary. BAML dosyasına derleyin. |
| **Kaynak** | WPF | Dosyayı *. g. resources* uzantısına sahip bir derleme bildirimi kaynak dosyasına katıştırmayı belirtir. |
| **Gölgeli** | .NET | Her satırda bir tane olmak üzere oluşturulan derleme dosya adlarının listesini içeren bir. accessor dosyası için kullanılır. Listedeki her derleme için, `ClassName_Accessor` yalnızca orijinallere benzeyen, ancak özel yöntemler yerine ortak yöntemlerle ortak sınıflar oluşturun. Birim testi için kullanılır. |
| **Giriş ekranı** | WPF | Uygulama başlatıldığında çalışma zamanında görüntülenecek bir resim dosyasını belirtir. |
| **XamlAppDef** | Windows Workflow Foundation | Derlemeyi, gömülü iş akışıyla bir derlemede iş akışı XAML dosyası oluşturmak için yönlendirir. |

> [!NOTE]
> Ek derleme eylemleri belirli proje türleri için tarafından tanımlanabilir, bu nedenle derleme eylemlerinin listesi proje türüne bağlıdır ve değerler bu listede yer alan görünebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic derleyici seçenekleri](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [derleme eylemleri (Mac için Visual Studio)](/visualstudio/mac/build-actions)
