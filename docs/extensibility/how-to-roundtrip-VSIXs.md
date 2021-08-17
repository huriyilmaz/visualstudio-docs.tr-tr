---
title: Uzantıları Gidiş Dönüş Olarak Gidiş Dönüş
description: Visual Studio 2015 ile Visual Studio 2019 veya 2017 arasında Visual Studio genişletilebilirlik projeleri Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: a5430271875917c890477a13e67056052ed382ee26546ef7536909866f0e8346
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401699"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Nasıl yapabilirsiniz: Uzantıların 2019/2017 Visual Studio 2015 ve Visual Studio uyumlu hale Visual Studio yapma

Bu belgede genişletilebilirlik projelerinin Visual Studio 2015 ile Visual Studio 2019 veya 2017 arasında gidiş dönüş Visual Studio açıklandı. Bu yükseltmeyi tamamladıktan sonra bir proje hem Visual Studio 2015 hem de Visual Studio 2019 veya 2017'de açabilecek, derleme, yükleme ve çalıştırabilecek. Başvuru olarak, Visual Studio 2015 ile Visual Studio 2019 veya 2017 arasında gidiş dönüş genişletilebilir bazı uzantılar VS SDK genişletilebilirlik [örneklerde bulunabilir.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

Yalnızca Visual Studio 2019/2017'de derlemek, ancak çıkış VSIX'in hem Visual Studio 2015 hem de Visual Studio 2019/2017'de çalışmasını istiyorsanız Uzantı geçişi belgesine [bakın.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

> [!NOTE]
> Sürümler arasında Visual Studio değişiklikler nedeniyle, bir sürümde çalışan bazı şeyler başka bir sürümde çalışmıyor. Erişmeye çalıştığınız özelliklerin her iki sürümde de kullanılabilir olduğundan emin olmak, yoksa uzantıda beklenmeyen sonuçlarla karşılaşabilirsiniz.

VsIX'i gidiş dönüş yapmak için bu belgede tamamlayılacak adımların ana hatları aşağıda velanmıştır:

1. Doğru veri NuGet içeri aktarın.
2. Uzantı Bildirimini Güncelleştir:
    * Yükleme hedefi
    * Önkoşullar
3. CSProj güncelleştirildi:
    * 'i `<MinimumVisualStudioVersion>` güncelleştirin.
    * özelliğini `<VsixType>` ekleyin.
    * Hata ayıklama özelliğini `($DevEnvDir)` 3 kez ekleyin.
    * Derleme araçlarını ve hedeflerini içeri aktarmaya yönelik koşullar ekleyin.

4. Derleme ve Test Etem

## <a name="environment-setup"></a>Ortamı ayarlama

Bu belgede makinenize aşağıdakilerin yüklü olduğu varsayıldı:

* Visual Studio SDK'nın yüklü olduğu 2015 sürümü
* Visual Studio Genişletilebilirlik iş yükü yüklü 2019 veya 2017

## <a name="recommended-approach"></a>Önerilen yaklaşım

Bu yükseltmeyi 2019 veya 2017'Visual Studio yerine Visual Studio 2015 ile başlatmanızı öneririz. Visual Studio 2015'te geliştirmenin temel avantajı, 2015'te mevcut olan derlemelere Visual Studio sağlamaktır. Visual Studio 2019 veya 2017'de geliştirme yapacaksanız, yalnızca Visual Studio 2019 veya 2017'de mevcut olan bir derlemeye bağımlılık uygulama riski vardır.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Üzerinde bir başvuru project.js

Bu belgenin devamında, **.csproj* dosyanıza koşullu içeri aktarma deyimleri ekleeceğiz. Bu, kaynak başvurularınızı NuGet içinde depolanıyorsa *project.jsçalışmaz.* Bu nedenle, tüm başvurular NuGet dosyanın *packages.config* önerilir.
Projeniz dosyada bir *project.jsiçeriyorsa:*

* üzerinde *project.js.*
* dosyasından **Çözüm Gezgini** *projedenproject.jsdosyasını* silin. Bu, *project.jsdosyasını* siler ve projeden kaldırır.
* NuGet başvurularını projeye geri ekleyin:
  * Çözüm'e sağ tıklayın **ve Çözüm** için NuGet **Paketlerini Yönet'i seçin.**
  * Visual Studio otomatik olarak *packages.config* dosya oluşturur.

> [!NOTE]
> Projeniz EnvDTE paketleri içeriyorsa, Başvuru ekle'yi seçerek ve  uygun başvuru ekleniyorsa Başvurular'a sağ tıklarsanız bunların ekleniyor olması gerekir.  NuGet paketlerin kullanımı, projenizi derlemeye çalışırken hatalara neden olabilir.

## <a name="add-appropriate-build-tools"></a>Uygun derleme araçları ekleme

Derlemeyi ve hata ayıklamayı uygun şekilde sağlayacak derleme araçlarını eklemeye dikkat etmek gerekir. Microsoft, bunun için Microsoft.VisualStudio.Sdk.BuildTasks adlı bir derleme oluşturdu.

Hem Visual Studio 2015 hem de 2019/2017'de VSIXv3 derlemek ve dağıtmak için aşağıdaki NuGet gerekir:

Sürüm | Yerleşik Araçlar
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2019 veya 2017 | Microsoft.VSSDK.BuildTool

Bunun için:

* Microsoft.VisualStudio.Sdk.BuildTasks.14.0 NuGet paketini projenize ekleyin.
* Projeniz Microsoft.VSSDK.BuildTools içeriyorsa ekleyin.
* Microsoft.VSSDK.BuildTools sürümünün 15.x veya daha büyük olduğundan emin olun.

## <a name="update-extension-manifest"></a>Uzantı bildirimini güncelleştirme

### <a name="1-installation-targets"></a>1. Yükleme hedefleri

VsIX Visual Studio hangi sürümleri hedefleymız olduğunu anlatmamız gerekiyor. Genellikle, bu başvurular sürüm 14.0 (Visual Studio 2015), sürüm 15.0 (Visual Studio 2017) veya sürüm 16.0 (Visual Studio 2019) olabilir. Bu durumda her iki sürüm için de uzantı yükecek bir VSIX oluşturmak istiyor, dolayısıyla her iki sürümü de hedeflememiz gerekiyor. VSIX'inizin 14.0'dan önceki sürümlerde derlemesi ve yüklemesi yapmak için önceki sürüm numarası ayar yapılabilir; ancak, sürüm 10.0 ve önceki sürümler artık desteklenmiyor.

* *source.extension.vsixmanifest dosyasını* Visual Studio.
* Hedefleri **Yükle sekmesini** açın.
* Sürüm  Aralığını [14.0, 17.0) olarak değiştirme. '[', Visual Studio 14.0'ın ve bunu geçen tüm sürümlerin dahil olduğunu söyler. ')' Visual Studio sürüm 17.0'a kadar olan ancak dahil olmak üzere tüm sürümleri dahil etmek zorunda olmadığını söyler.
* Tüm değişiklikleri kaydedin ve uygulamanın tüm Visual Studio.

![Yükleme Hedefleri Görüntüsü](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. *extension.vsixmanifest dosyasına Önkoşullar* Ekleme

Önkoşul olarak Visual Studio Core Editor'a ihtiyacımız var. Ön Visual Studio eklemek için güncelleştirilmiş bildirim tasarımcısını kullanın.

Bunu el ile yapmak için:

* Dosya Gezgini'da proje dizinine gidin.
* *extension.vsixmanifest dosyasını bir* metin düzenleyicisiyle açın.
* Aşağıdaki etiketi ekleyin:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Dosyayı kaydedin ve kapatın.

> [!NOTE]
> 2019 veya 2017'nin tüm sürümleriyle uyumlu olduğundan emin olmak için Önkoşul sürümünü el ile Visual Studio gerekebilir. Bunun nedeni tasarımcının en düşük sürümü geçerli sürüm olarak eklemesi Visual Studio (örneğin, 15.0.26208.0). Ancak, diğer kullanıcılar daha önceki bir sürüme sahip olabilir, bu sürümü 15.0'a el ile düzenlemek gerekir.

Bu noktada bildirim dosyanız şuna benzer şekilde görünüyor:

![Önkoşul Örneği](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Proje dosyasını değiştirme (myproject.csproj)

Bu adımı yaparken değiştirilmiş bir .csproj'a başvuru açılması kesinlikle önerilir. Burada birkaç örnek [bulabilirsiniz.](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Herhangi bir genişletilebilirlik örneğini seçin, başvuru için *.csproj* dosyasını bulun ve aşağıdaki adımları yürütün:

* dizininde proje dizinine **Dosya Gezgini.**
* *myproject.csproj dosyasını bir* metin düzenleyicisiyle açın.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. MinimumVisualStudioVersion Güncelleştirme

* En düşük Visual Studio sürümünü olarak ayarlayın `$(VisualStudioVersion)` ve buna bir koşullu deyim ekleyin. Bu etiketleri yoksa ekleyin. Etiketlerin aşağıda olduğu gibi ayarlanmıştır:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. VsixType özelliğini ekleyin.

* Bir özellik grubuna `<VsixType>v3</VsixType>` aşağıdaki etiketi ekleyin.

> [!NOTE]
> Bunu etiketinin altına eklemeniz `<OutputType></OutputType>` önerilir.

### <a name="3-add-the-debugging-properties"></a>3. Hata ayıklama özelliklerini ekleme

* Aşağıdaki özellik grubunu ekleyin:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Aşağıdaki kod örneğinin tüm örneklerini *.csproj dosyasından* ve *.csproj.user dosyalarından* silin:

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Derleme araçları içeri aktarmalara koşullar ekleme

* `<import>`Microsoft.VSSDK.BuildTools başvurusu olan etiketlere ek koşullu deyimler ekleyin. Koşul `'$(VisualStudioVersion)' != '14.0' And` deyiminin önüne ekleme. Bu deyimler csproj dosyasının üst bilgisinde ve alt bilgisinde görünür.

Örnek:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* `<import>`Microsoft.VisualStudio.Sdk.BuildTasks.14.0 olan etiketlere ek koşullu deyimler ekleyin. Koşul `'$(VisualStudioVersion)' == '14.0' And` deyiminin önüne ekleme. Bu deyimler csproj dosyasının üst bilgisinde ve alt bilgisinde görünür.

Örnek:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* `<Error>`Microsoft.VSSDK.BuildTools başvurusu olan etiketlere ek koşullu deyimler ekleyin. Bunu yapmak için condition `'$(VisualStudioVersion)' != '14.0' And` deyiminin önüne eklersiniz. Bu deyimler csproj dosyasının alt bilgisinde görünür.

Örnek:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* `<Error>`Microsoft.VisualStudio.Sdk.BuildTasks.14.0 olan etiketlere ek koşullu deyimler ekleyin. Koşul `'$(VisualStudioVersion)' == '14.0' And` deyiminin önüne ekleme. Bu deyimler csproj dosyasının alt bilgisinde görünür.

Örnek:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* csproj dosyasını kaydedin ve kapatın. 
  * Çözümde birden fazla proje kullanıyorsanız, proje bağlam menüsünde "Başlangıç Project Olarak Ayarla" seçeneğini kullanarak bu projeyi Başlangıç Project olarak ayarlayın). Bu, Visual Studio kaldırılan projenin yeniden açılmasını sağlar.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Visual Studio 2015 ve 2019 veya 2017 Visual Studio yüklemelerini test etmek

Bu noktada projeniz hem 2015 hem de 2017'de Visual Studio VSIXv3 Visual Studio hazır olur.

* Projenizi 2015 Visual Studio açın.
* Projenizi derleme ve çıkışta VSIX'in doğru şekilde derlemesini onaylayın.
* Proje dizininize gidin.
* *\bin\Debug klasörünü* açın.
* VSIX dosyasına çift tıklayın ve uzantınızı Visual Studio 2015 ve 2019/2017 Visual Studio yükleyin.
* Uzantıyı Yüklü bölümündeki Araçlar Uzantıları  >  **ve Güncelleştirmeler bölümünde gördüğünüzden** **emin** olun.
* Çalıştığını kontrol etmek için uzantıyı çalıştırmayı/kullanmayı deneme.

![VSIX bulma](media/finding-a-VSIX-example.png)

> [!NOTE]
> Projeniz dosyasını açma iletisiyle yanıt **vermezse,** dosyayı kapatmaya Visual Studio, proje dizininize gidin, gizli klasörleri gösterir ve *.vs klasörünü* silin.
