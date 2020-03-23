---
title: Dosyalar için eylemler oluşturma
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301988"
---
# <a name="build-actions"></a>Derleme eylemleri

Visual Studio projesindeki tüm dosyaların bir yapı eylemi var. Yapı eylemi, proje derlendiğinde dosyaya ne olacağını denetler.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'da oluşturma eylemleri'ne](/visualstudio/mac/build-actions)bakın.

## <a name="set-a-build-action"></a>Yapı eylemi ayarlama

Bir dosya için yapı eylemini ayarlamak için, **Solution Explorer'da** dosyayı seçip **Alt**+**Enter**tuşuna basarak **Dosyanın Özelliklerini** penceresinde açın. Veya **Solution Explorer'daki** dosyaya sağ tıklayın ve **Özellikler'i**seçin. **Özellikler** penceresinde, **Gelişmiş** bölümün altında, dosya için bir yapı eylemi ayarlamak için **Eylem Oluştur'un** yanındaki açılır listeyi kullanın.

![Visual Studio'da bir dosya için eylemler oluşturma](media/build-actions.png)

## <a name="build-action-values"></a>Eylem değerleri oluşturma

C# ve Visual Basic proje dosyaları için daha yaygın yapı eylemlerinden bazıları şunlardır:

|Eylem Oluştur | Proje türleri | Açıklama |
|-|-|
| **Ek Dosyalar** | C#, Visual Basic | C# veya Visual Basic derleyicisine giriş olarak geçirilen kaynak olmayan bir metin dosyası. Bu yapı eylemi esas olarak kod kalitesini doğrulamak için bir proje tarafından başvurulan [çözümleyicilere](../code-quality/roslyn-analyzers-overview.md) giriş sağlamak için kullanılır. Daha fazla bilgi için [bkz.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md)|
| **Uygulama Tanımı** | WPF | Uygulamanızı tanımlayan dosya. Bir projeyi ilk oluşturduğunuzda, bu *App.xaml'dır.* |
| **CodeAnalysisDictionary** | .NET | Yazım denetimi için Kod Analizi tarafından kullanılan özel bir sözcük sözlüğü. [Bkz. Nasıl: Kod Analizi Sözlüğü'ni özelleştirin](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Derlemek** | herhangi bir | Dosya derleyiciye kaynak dosya olarak aktarılır.|
| **İçerik** | .NET | **İçerik** olarak işaretlenmiş bir dosya, 'yi <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>arayarak akış olarak alınabilir. ASP.NET projeleriçin bu dosyalar dağıtıldığında sitenin bir parçası olarak bulunur.|
| **Tasarım Verileri** | WPF | XAML ViewModel dosyaları için kullanılır, kullanıcı denetimlerinin tasarım zamanında, sahte türleri ve örnek verilerle görüntülenebilmesi için. |
| **DesignDataWithDesignTimeCreateable** | WPF | **DesignData**gibi, ancak gerçek türleri ile.  |
| **Gömülü Kaynak** | .NET | Dosya derlemeye katıştırılması gereken bir kaynak olarak derleyiciye geçirilir. Dosyayı <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> derlemeden okumak için arayabilirsiniz.|
| **EntityDeploy** | .NET | Varlık Çerçevesi (EF) için .EF yapılarının dağıtımını belirten edmx dosyaları. |
| **Sahte** | .NET | Microsoft Fakes test çerçevesi için kullanılır. [Microsoft Fakes kullanarak testi n altında kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Yok** | herhangi bir | Dosya herhangi bir şekilde yapının bir parçası değildir. Bu değer, örneğin "ReadMe" dosyaları gibi belge dosyaları için kullanılabilir.|
| **Sayfası** | WPF | Çalışma zamanında daha hızlı yüklemek için bir XAML dosyasını ikili .baml dosyasına derle. |
| **Kaynak** | WPF | Dosyayı uzantısı *.g.resources*olan bir derleme bildirimi kaynak dosyasına katıştırmak için belirtir. |
| **Gölge** | .NET | Yapılı derleme dosya adlarının listesini içeren bir .accessor dosyası için, satır başına bir tane kullanılır. Listedeki her derleme için, orijinallere `ClassName_Accessor` benzeyen adlarla, ancak özel yöntemler yerine ortak yöntemlerle ortak sınıflar oluşturun. Birim testi için kullanılır. |
| **Giriş Ekranı** | WPF | Uygulama başlatılırken çalışma zamanında görüntülenecek bir resim dosyası belirtir. |
| **XamlAppDef** | Windows Workflow Foundation | Yapıya, katışmış iş akışı olan bir derlemeye iş akışı XAML dosyası oluşturmatalimatı verir. |

> [!NOTE]
> Ek yapı eylemleri belirli proje türleri için tanımlanabilir, bu nedenle yapı eylemleri listesi proje türüne bağlıdır ve bu listede olmayan değerler görünebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic derleyici seçenekleri](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Eylemler oluşturma (Mac için Visual Studio)](/visualstudio/mac/build-actions)
