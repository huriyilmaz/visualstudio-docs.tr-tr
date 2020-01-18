---
title: Uzantıları gidiş dönüş
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: d6de945e7221d2239e1b4f00185a5b16c04b717d
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269057"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Nasıl yapılır: Visual Studio 2019/2017 ve Visual Studio 2015 ile uyumlu uzantılar yapma

Bu belgede, Visual Studio 2015 ile Visual Studio 2019 veya Visual Studio 2017 arasında genişletilebilirlik projelerinin nasıl gezilebileceği açıklanmaktadır. Bu yükseltmeyi tamamladıktan sonra, bir proje hem Visual Studio 2015 hem de Visual Studio 2019 ya da 2017 içinde açabilir, oluşturabilir, kurabilir ve çalıştırılabilir. Başvuru olarak, Visual Studio 2015 ile Visual Studio 2019 veya 2017 arasında gidiş dönüş sağlayan bazı uzantılar [vs SDK genişletilebilirlik örneklerinde](https://github.com/Microsoft/VSSDK-Extensibility-Samples)bulunabilir.

Yalnızca Visual Studio 2019/2017 ' de derlemeyi planlıyorsanız, ancak çıktı VSıX 'in hem Visual Studio 2015 hem de Visual Studio 2019/2017 ' de çalıştırılmasını istiyorsanız [uzantı geçiş belgesine](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)bakın.

> [!NOTE]
> Sürümler arasında Visual Studio 'daki değişiklikler nedeniyle, bir sürümde çalışan bazı şeyler başka bir sürümde çalışmaz. Erişmeye çalıştığınız özelliklerin her iki sürümde de kullanılabildiğinden emin olun, aksi durumda uzantı beklenmedik sonuçlara neden olur.

Bu belgede, bir VSıX 'i yuvarlamak için tamamlayacağımız adımların bir ana hattı aşağıda verilmiştir:

1. Doğru NuGet paketlerini içeri aktarın.
2. Uzantı bildirimini güncelleştir:
    * Yükleme hedefi
    * Prerequisites
3. CSProj güncelleştir:
    * Güncelleştirme `<MinimumVisualStudioVersion>`.
    * `<VsixType>` özelliğini ekleyin.
    * 3 kez `($DevEnvDir)` hata ayıklama özelliğini ekleyin.
    * Derleme araçlarını ve hedefleri içeri aktarmaya yönelik koşullar ekleyin.

4. Derleme ve Test Etem

## <a name="environment-setup"></a>Ortam kurulumu

Bu belge, makinenizde aşağıdakilerin yüklü olduğunu varsayar:

* VS SDK yüklü Visual Studio 2015
* Genişletilebilirlik iş yükünün yüklü olduğu Visual Studio 2019 veya 2017

## <a name="recommended-approach"></a>Önerilen yaklaşım

Visual Studio 2019 veya 2017 yerine Visual Studio 2015 ile bu yükseltmeyi başlatmak önemle önerilir. Visual Studio 2015 ' de geliştirmesinin başlıca avantajı, Visual Studio 2015 ' de bulunmayan derlemelere başvurmatığınızdan emin olunması sağlamaktır. Visual Studio 2019 veya 2017 ' de geliştirme yaparsanız, yalnızca Visual Studio 2019 veya 2017 sürümünde bulunan bir derlemeye bağımlılık getirebilmeniz riski vardır.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Project. JSON öğesine başvuru olmadığından emin olun

Bu belgede daha sonra, * *. csproj* dosyanıza koşullu içeri aktarma deyimleri ekleyeceğiz. NuGet başvurularınız *Project. JSON*içinde depolanıyorsa bu çalışmaz. Bu nedenle, tüm NuGet başvurularını *Packages. config* dosyasına taşımanız önerilir.
Projeniz bir *Project. JSON* dosyası içeriyorsa:

* *Project. JSON*' daki başvuruları bir yere göz atın.
* **Çözüm Gezgini**, projeden *Project. JSON* dosyasını silin. Bu, *Project. JSON* dosyasını siler ve projeden kaldırır.
* NuGet başvurularını projeye geri ekleyin:
  * **Çözüme** sağ tıklayın ve **çözüm Için NuGet Paketlerini Yönet**' i seçin.
  * Visual Studio, sizin için *Packages. config* dosyasını otomatik olarak oluşturur.

> [!NOTE]
> Projeniz EnvDTE paketleri içeriyorsa, **Başvuru Ekle** **' yi seçerek ve** uygun başvuruyu ekleyerek eklenmeleri gerekebilir. NuGet paketlerinin kullanılması, projenizi oluşturmaya çalışırken hata oluşturabilir.

## <a name="add-appropriate-build-tools"></a>Uygun derleme araçlarını ekleyin

Uygun şekilde derleme ve hata ayıklama yapmamızı sağlayacak derleme araçları eklememiz gerekiyor. Microsoft, Microsoft. VisualStudio. SDK. BuildTasks adlı bir derleme oluşturdu.

Hem Visual Studio 2015 hem de 2019/2017 ' de bir Vsıxv3 oluşturup dağıtmak için aşağıdaki NuGet paketlerini yapmanız gerekir:

Sürüm | Oluşturulan Araçlar
--- | ---
Visual Studio 2015 | Microsoft. VisualStudio. SDK. BuildTasks. 14.0
Visual Studio 2019 veya 2017 | Microsoft. VSSDK. BuildTool

Bunu yapmak için:

* Projenize Microsoft. VisualStudio. SDK. BuildTasks. 14.0 NuGet paketini ekleyin.
* Projeniz Microsoft. VSSDK. BuildTools içermiyorsa, ekleyin.
* Microsoft. VSSDK. BuildTools sürümünün 15. x veya daha büyük olduğundan emin olun.

## <a name="update-extension-manifest"></a>Uzantı bildirimini Güncelleştir

### <a name="1-installation-targets"></a>1. Yükleme hedefleri

Visual Studio 'ya bir VSıX oluşturmak için hangi sürümlerin hedefleyeceğinizi söylememiz gerekir. Genellikle, bu başvurular sürüm 14,0 (Visual Studio 2015), sürüm 15,0 (Visual Studio 2017) veya sürüm 16,0 (Visual Studio 2019) ' ya kadar. Bizim örneğimizde, her ikisi için de bir uzantı yükleyecek bir VSıX oluşturmak istiyoruz, bu nedenle her iki sürümü de hedefliyoruz. VSıX 'in 14,0 ' den önceki sürümlerde oluşturup yüklemesini istiyorsanız bu, önceki sürüm numarası ayarlanarak yapılabilir; Ancak, sürüm 10,0 ve önceki sürümleri artık desteklenmemektedir.

* Visual Studio 'da *Source. Extension. valtmanifest* dosyasını açın.
* **Hedefleri yüklensin** sekmesini açın.
* **Sürüm aralığını** [14,0, 17,0) olarak değiştirin. ' [', Visual Studio 'Nun 14,0 ve bu sürümü aşan tüm sürümleri içermesini söyler. ') ', Visual Studio 'Nun sürüm 17,0 ' ye kadar olan tüm sürümleri dahil etmek üzere söylemasını söyler.
* Tüm değişiklikleri kaydedin ve Visual Studio 'nun tüm örneklerini kapatın.

![Yükleme hedefi görüntüsü](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. *uzantı. valtmanifest* dosyasına Önkoşullar ekleniyor

Önkoşul olarak Visual Studio Core Düzenleyicisi gerekir. Visual Studio 'Yu açın ve önkoşulları eklemek için güncelleştirilmiş bildirim tasarımcısını kullanın.

Bunu el ile yapmak için:

* Dosya Gezgini 'nde proje dizinine gidin.
* *Extension. valtmanifest* dosyasını bir metin düzenleyicisiyle açın.
* Aşağıdaki etiketi ekleyin:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Dosyayı kaydedin ve kapatın.

> [!NOTE]
> Tüm Visual Studio 2019 veya 2017 sürümleriyle uyumlu olduğundan emin olmak için önkoşul sürümünü el ile düzenlemeniz gerekebilir. Bunun nedeni, tasarımcının en düşük sürümü Visual Studio 'nun geçerli sürümünüz olarak (örneğin, 15.0.26208.0) ekleyecektir. Ancak, diğer kullanıcıların önceki bir sürümü olabileceğinden, bunu 15,0 olarak el ile düzenlemeniz gerekir.

Bu noktada, bildirim dosyanız şuna benzer görünmelidir:

![Önkoşul örneği](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Proje dosyasını değiştirme (MyProject. csproj)

Bu adım yapılırken değiştirilmiş. csproj açık öğesine bir başvuruya sahip olmanız kesinlikle önerilir. [Burada](https://github.com/Microsoft/VSSDK-Extensibility-Samples)birkaç örnek bulabilirsiniz. Herhangi bir genişletilebilirlik örneği seçin, başvuru için *. csproj* dosyasını bulun ve aşağıdaki adımları yürütün:

* **Dosya Gezgini**'nde proje dizinine gidin.
* *MyProject. csproj* dosyasını bir metin düzenleyicisiyle açın.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. MinimumVisualStudioVersion güncelleştirin

* En düşük Visual Studio sürümünü `$(VisualStudioVersion)` olarak ayarlayın ve bunun için koşullu bir ifade ekleyin. Mevcut değilse bu etiketleri ekleyin. Etiketlerin aşağıdaki gibi ayarlandığından emin olun:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Valttype özelliğini ekleyin.

* Aşağıdaki etiketi `<VsixType>v3</VsixType>` bir özellik grubuna ekleyin.

> [!NOTE]
> Bunu `<OutputType></OutputType>` etiketinin altına eklemeniz önerilir.

### <a name="3-add-the-debugging-properties"></a>3. hata ayıklama özelliklerini ekleyin

* Aşağıdaki özellik grubunu ekleyin:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Aşağıdaki kod örneğinin tüm örneklerini *. csproj* dosyasından ve *. csproj. User* dosyalarından silin:

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. derleme araçları içeri aktarmaları için koşullar ekleyin

* Microsoft. VSSDK. BuildTools başvurusuna sahip `<import>` etiketlere ek koşullu deyimler ekleyin. Koşul ifadesinin önüne `'$(VisualStudioVersion)' != '14.0' And` ekleyin. Bu deyimler, csproj dosyasının üst bilgisinde ve altbilgisinde görünür.

Örneğin:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Microsoft. VisualStudio. SDK. BuildTasks. 14.0 içeren `<import>` etiketlere ek koşullu deyimler ekleyin. Koşul ifadesinin önüne `'$(VisualStudioVersion)' == '14.0' And` ekleyin. Bu deyimler, csproj dosyasının üst bilgisinde ve altbilgisinde görünür.

Örneğin:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Microsoft. VSSDK. BuildTools başvurusuna sahip `<Error>` etiketlere ek koşullu deyimler ekleyin. Bunu, koşul ifadesinin önüne `'$(VisualStudioVersion)' != '14.0' And` ekleyerek yapın. Bu deyimler csproj dosyasının altbilgisinde görünür.

Örneğin:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Microsoft. VisualStudio. SDK. BuildTasks. 14.0 içeren `<Error>` etiketlere ek koşullu deyimler ekleyin. Koşul ifadesinin önüne `'$(VisualStudioVersion)' == '14.0' And` ekleyin. Bu deyimler csproj dosyasının altbilgisinde görünür.

Örneğin:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Csproj dosyasını kaydedin ve kapatın. 
  * Çözümde birden fazla proje kullanıyorsanız, proje bağlam menüsünde "başlangıç projesi olarak ayarla" seçeneğini kullanarak bu projeyi başlangıç projesi olarak ayarlayın. Bu, Visual Studio 'Yu kaldırdıktan sonra bu projeyi yeniden açmasını sağlar.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Visual Studio 2015 ve Visual Studio 2019 veya 2017 ' de Uzantı yüklemelerini test edin

Bu noktada, projeniz hem Visual Studio 2015 hem de Visual Studio 2017 üzerine yükleyebileceğiniz bir Vsıxv3 oluşturmaya hazırlanmalıdır.

* Projenizi Visual Studio 2015 ' de açın.
* Projenizi derleyin ve bir VSıX 'in doğru bir şekilde derlemelerin çıktıda onaylayın.
* Proje dizininize gidin.
* *\Bin\debug* klasörünü açın.
* VSıX dosyasına çift tıklayın ve uzantınızı Visual Studio 2015 ve Visual Studio 2019/2017 ' ye yükler.
* Uzantıyı, **yüklü** bölümünde yer alan **Araçlar** > **Uzantılar ve güncelleştirmeler** ' de görediğinizden emin olun.
* Çalıştığını denetlemek için uzantıyı çalıştırmayı/kullanmayı deneyin.

![VSıX bulma](media/finding-a-VSIX-example.png)

> [!NOTE]
> Projeniz **dosyayı açan**iletiyle askıda kalırsa, Visual Studio 'yu kapatmayı zorla, proje dizininiz ' ne gidin, gizli klasörleri gösterin ve *. vs* klasörünü silin.
 
