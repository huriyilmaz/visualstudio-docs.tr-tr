---
title: Bir projedeki başvuruları yönetme
description: Bir projedeki dış bileşenlere ve bağlı hizmetlere yapılan başvuruları yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a33dcd7d6d6f3dfc045951a4533b6aae8e9ee0af
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152022"
---
# <a name="manage-references-in-a-project"></a>Bir projedeki başvuruları yönetme

Bir dış bileşene veya bağlı hizmete karşı kod yazmadan önce projenizin önce buna bir başvuru içermesi gerekir. Başvuru temelde, bileşeni veya hizmeti bulmak için gereken bilgileri Visual Studio proje dosyasındaki bir giriştir.

Başvuru eklemek için, dosyanın  içinde Başvurular veya **Bağımlılıklar düğümüne** sağ **tıklayın ve Çözüm Gezgini** Ekle'yi **seçin.** Ayrıca proje düğümüne sağ tıklar ve Başvuru **Ekle'yi de**  >  **seçersiniz.** Daha fazla bilgi için, [bkz. How to: Add or remove references](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Visual C kılavuzuna başvuru&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Aşağıdaki bileşen ve hizmet türlerine başvuru eklemek için:

- .NET sınıf kitaplıkları veya derlemeleri

- UWP uygulamaları

- COM bileşenleri

- Aynı çözümde yer alan projelerin diğer derlemeleri veya sınıf kitaplıkları

- Paylaşılan projeler

- XML Web hizmetleri

## <a name="uwp-app-references"></a>UWP uygulama başvuruları

### <a name="project-references"></a>Proje başvuruları

Evrensel Windows Platformu (UWP) projeleri, çözümdeki diğer UWP projelerine veya bu projelerin Windows 10'de kullanım dışı olan API'leri kullanmama şartıyla çözümdeki diğer UWP projelerine veya Windows 8.1 projelerine veya ikililere başvurular oluşturabilir. Daha fazla bilgi için [bkz. Windows Runtime 8'den UWP'ye taşıma.](/windows/uwp/porting/w8x-to-uwp-root)

Yeni projelerin hedeflerini yeniden Windows 8.1 seçerseniz bkz. Windows 10 projelerini [taşıma, geçirme ve Visual Studio yükseltme.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

### <a name="extension-sdk-references"></a>Uzantı SDK'sı başvuruları

Visual Basic, C#, C++ ve JavaScript Evrensel Windows Platformu (UWP) uygulamaları, bu Uzantı SDK'ları Windows 8.1'de kullanım dışı olan API'leri kullanmamaları sürece Windows 10. UWP uygulamaları tarafından başvurulıp başvurulablanı olmadığını bulmak için lütfen Uzantı SDK'sı satıcı sitesine bakın.

Uygulamanıza başvurulan Uzantı SDK'sı'nın destekçi olmadığını belirlersanız aşağıdaki adımları gerçekleştirmeniz gerekir:

1. Hataya neden olan projenin adına bakın. Projenizin hedeflemektedir platformu, proje adının yanındaki parantez içinde not edildi. Örneğin, **MyProjectName (Windows 8.1),** **ProjemProjectName** projenizin platform sürümünü hedeflemektedir Windows 8.1.

1. Desteklenmeyen Uzantı SDK'sı sahibi olan satıcının sitesine gidin ve Uzantı SDK'sı sürümünü projenizin hedeflemiş olduğu platformun sürümüyle uyumlu bağımlılıklarla yükleyin.

    > [!NOTE]
    > Uzantı SDK'sı diğer Uzantı SDK'larında bağımlılıkları olup olmadığını bulmanın bir yolu Başvuru Yöneticisi'ne **bakarakdır.** Yeniden Visual Studio, yeni bir C# UWP uygulama projesi oluşturun, sonra projeye sağ tıklayın ve Başvuru **Ekle'yi seçin.** Windows **sekmesine,** ardından **Uzantılar** alt sekmesine gidin ve Uzantı SDK'sı'yı seçin. Başvuru Yöneticisi'nde sağ **bölmeye bakın.** Bağımlılıkları varsa bunlar orada listelenir.

    > [!IMPORTANT]
    > Projeniz Windows 10'i hedeflese ve önceki adımda yüklü olan Uzantı SDK'sı Microsoft Visual C++ Çalışma Zamanı Paketi'ne bağımlı ise, Microsoft Visual C++ Çalışma Zamanı Paketi'nin Windows 10 ile uyumlu sürümü v14.0'dır ve Visual Studio ile yüklenir.

1. Önceki adımda yüklü olan Uzantı SDK'sı diğer Uzantı SDK'larına bağımlılıklara sahipse, bağımlılıklara sahip satıcıların sitelerine gidin ve bu bağımlılıkların projenizin hedeflemektedir platform sürümüyle uyumlu sürümlerini yükleyin.

1. Uygulamayı Visual Studio ve açın.

1. Hataya neden olan **projedeki Başvurular** **veya** Bağımlılıklar düğümüne sağ tıklayın ve Başvuru Ekle'yi **seçin.**

1. Yeni **Windows** sekmesine ve  ardından Uzantılar alt sekmesine tıklayın, ardından eski Uzantı SDK'ları için onay kutularının işaretini kaldırın ve yeni UzantıDK'ları için onay kutularını işaretleyin. **Tamam**'a tıklayın.

## <a name="add-a-reference-at-design-time"></a>Tasarım zamanında başvuru ekleme

Projeniz içinde bir derlemeye başvuruda Visual Studio aşağıdaki konumlarda derlemeyi arar:

- Geçerli proje dizini. (Gözat sekmesini kullanarak bu **derlemeleri** bulabilirsiniz.)

- Aynı çözümde yer alan diğer proje dizinleri. (Bu derlemeleri Projeler sekmesinde **bulabilirsiniz.)**

> [!NOTE]
> - Tüm projeler **mscorlib** için örtülü bir başvuru içerir.
> - Tüm projeler, başvuru listesinden `System.Core` kaldırılmış olsa `System.Core` bile için örtülü bir başvuru içerir.
> - Visual Basic projeleri için örtük bir başvuru <xref:Microsoft.VisualBasic> içerir.

## <a name="references-to-shared-components-at-run-time"></a>Çalışma zamanında paylaşılan bileşenlere başvurular

Çalışma zamanında, bileşenlerin projenin çıkış yolunda veya Genel Derleme Önbelleği'nde (GAC) olması gerekir. Proje bu konumlardan biri içinde yer alan bir nesneye başvuru içeriyorsa, projeyi derlemek için başvurudan projenin çıkış yoluna kopyalamanız gerekir. özelliği, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> bu kopyanın yapılmış olup olmadığını gösterir. Değer True **ise,** projeyi derlemeniz için başvuru proje dizinine kopyalanır. Değer False **ise,** başvuru kopyalanmaz.

GAC'de kayıtlı özel bir bileşene başvuru içeren bir uygulama dağıtırsanız, bileşen ayardan bağımsız olarak uygulamayla birlikte <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> dağıtilmez. Derlemenin önceki Visual Studio, derlemenin dağıtıldığından emin olmak için bir başvuru <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> üzerinde özelliğini ayarlayın. Şimdi derlemeyi \Bin klasörüne el ile eklemeniz gerekir. Bu, tüm özel kodu irdeler ve tanıdık olmadığınız özel kod yayımlama riskini azaltarak.

Varsayılan olarak, derleme veya bileşen genel derleme önbelleğinde veya bir çerçeve bileşeni ise <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> özelliği **False** olarak ayarlanır. Aksi takdirde değer True olarak **ayarlanır.** Project proje başvuruları her zaman True olarak **ayarlanır.**

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>Farklı bir .NET sürümünü hedef alan bir projeye veya derlemeye başvuru

.NET'in farklı bir sürümünü hedef alan projelere veya derlemelere başvurulan uygulamalar oluşturabilirsiniz. Örneğin, 4.5'i .NET Framework bir derlemeye başvuran bir .NET Framework oluşturabilirsiniz. .NET'in önceki bir sürümünü hedef alan bir proje oluşturmanız, bu projedeki bir başvuru için daha yeni bir sürümü hedef alan bir proje veya derleme ayaramaz.

Daha fazla bilgi için [bkz. Çerçeve hedeflemeye genel bakış.](../ide/visual-studio-multi-targeting-overview.md)

## <a name="project-to-project-references"></a>Project-proje başvuruları

Project-proje başvuruları, derlemeleri içeren projelere başvurulardır; Proje başvurularını, Başvuru Yöneticisi **iletişim kutusunun** Projeler sekmesini kullanarak eklersiniz. Visual Studio yolu verilen bir derlemeyi bulabilirsiniz.

Derleme üreten bir projeniz olduğunda, projeye başvurarak bir dosya başvurusu kullanmamanız gerekir (aşağıya bakın). Projeden projeye başvurularının avantajı, derleme sistemideki projeler arasında bir bağımlılık oluşturmasıdır. Bağımlı proje, başvuran projenin en son 4. kez 4. kez 4. kez 4. kez 4. kez 4. kez 4. kez 4. kez 4. kez 4. kez 4. sırada yer alan bir projedir. Dosya başvurusu derleme bağımlılığı oluşturmaz, bu nedenle bağımlı projeyi oluşturmadan başvuran projeyi derlemek mümkündür ve başvuru artık kullanılamaz. (Başka bir ifadeyle, proje projenin daha önce yapılmış bir sürümüne başvurur.) Bu, bin dizininde tek bir DLL'nin birkaç sürümünün gerekli olmasıyla sonuçlanabiliyor ve bu mümkün değildir.  Bu çakışma oluştuğunda "Uyarı: 'proje' projesinde 'dosya' bağımlılığı run dizinine kopyalanamaz çünkü 'file.' başvurusu üzerine yazabilir" gibi bir ileti alırsınız. Daha fazla bilgi için [bkz. Bozuk başvurularla ilgili sorunları giderme](../ide/troubleshooting-broken-references.md) [ve Nasıl 2. Adım: Proje bağımlılıkları oluşturma ve kaldırma.](../ide/how-to-create-and-remove-project-dependencies.md)

> [!NOTE]
> Bir projenin hedef sürümü .NET Framework sürüm 4.5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3.5 veya 4.0 ise projeden projeye başvuru yerine bir dosya başvurusu oluşturulur.

## <a name="shared-project-references"></a>Paylaşılan proje başvuruları

Diğer çoğu proje türüne *göre, paylaşılan bir proje* hiçbir ikili çıkışa sahip değildir. Bunun yerine, kod buna başvurulan her projede derlenmiş olur. [Paylaşılan Projeler,](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) bir dizi farklı uygulama projesi tarafından başvurulan ortak kod yazmana izin verir. Kod, başvuran her projenin parçası olarak derlenmiştir ve platforma özgü işlevleri paylaşılan kod tabanına dahil etmeye yardımcı olmak için derleyici yönergelerini içerebilir. Başvuru Yöneticisi iletişim kutusunun Paylaşılan Projeler **sekmesinde paylaşılan** bir projeye başvuru ekleyin.

## <a name="file-references"></a>Dosya başvuruları

Dosya başvuruları, bir derleme projesinin bağlamı dışındaki derlemelere doğrudan Visual Studio başvurudur. Bunları, Başvuru Yöneticisi iletişim **kutusunun** Gözat sekmesini kullanarak oluşturabilirsiniz. Yalnızca bir derlemeniz veya bileşeniniz olduğunda ve bunu çıkış olarak oluşturan projeye sahip değilken bir dosya başvurusu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bozuk başvurularda sorun giderme](../ide/troubleshooting-broken-references.md)
- [Nasıl yapılanlar: Başvuru ekleme veya kaldırma](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
