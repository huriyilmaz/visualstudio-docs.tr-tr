---
title: Visual Studio 2022 önizlemesinde apı değişiklikleri kesiliyor
description: uzantıları Visual Studio 2022 önizlemesine geçirirken mevcut VS uzantılarının derleyememesine neden olan apı değişiklikleri hakkında bilgi edinin.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: fd2f1661f57cc0e03dfa1a543d9ae1be0a1e0163
ms.sourcegitcommit: 3c5b1a1d51b521356f42a6879c1f1745573dda65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2021
ms.locfileid: "114592274"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Visual Studio 2022 ' de apı değişiklikleri kesiliyor

[!INCLUDE [preview-note](../includes/preview-note.md)]

bir uzantıyı Visual Studio 2022 ' ye geçiriyorsanız burada listelenen son değişiklikler sizi etkileyebilir.

## <a name="reference-assemblies-no-longer-installed"></a>Başvuru derlemeleri artık yüklenmedi

Visual Studio yükleme dizininden çözümlenen MSBuild başvuran derlemelerin birçoğu artık yüklü değil. ihtiyaç duyduğunuz Visual Studio SDK başvuru derlemelerini almak için NuGet kullanmanız gerekir. Bunu yapmakla ilgili ayrıntılı adımlar için bkz. [modernleştirin Projects](update-visual-studio-extension.md#modernize-your-vsix-project) .

## <a name="removed-apis"></a>Kaldırılan API 'Ler

Visual Studio 2022 ' de, Visual Studio taşımaya yönelik bir parçası olarak bazı apı 'ler kaldırılmıştır. Kaldırılan API 'lerin listesi, [kaldırılan API listesi](removed-api-list.md) sayfasında bulunabilir.

## <a name="interop-breaking-changes"></a>Birlikte çalışma son değişiklikleri

apı 'lerimizin birçoğu, genellikle kodunuzun uyum sağlaması için basit değişikliklerle birlikte Visual Studio 2022 ' de değişmiştir.

Son değişiklikleri yönetmek için birlikte çalışma derlemelerinin dağıtılması için yeni bir mekanizma sağlamayı planlıyoruz. özellikle, Visual Studio 2022 ve ötesinde, birçok ortak ortak Visual Studio arabirimine yönelik tanımlarla birlikte tek bir birlikte çalışma derlemesi sağlıyoruz. bu derleme, birden fazla birlikte çalışma derlemesinden uzaklaşarak birçok Visual Studio arabirimi için yönetilen tanımlar içerir. yeni birlikte çalışma derlemesi `Microsoft.VisualStudio.Interop` NuGet paketi aracılığıyla dağıtılır.

bununla birlikte, öncelikle yerel bağlamlarda kullanılan ve az sayıda son değişiklik içeren Visual Studio bileşenleri kendi birlikte çalışma derlemelerine sahip olmaya devam eder (örneğin, hata ayıklayıcı derlemesi bugün devam ettiği için yine de VisualStudio.Debugger.Interop.dll olur). Her durumda, bu derlemeler bugün olduğu gibi, uygulamanız tarafından daha sonra başvurulabilirler.

bu önemli bir değişiklik ve içindeki apı 'leri kullanan ve bu yeni yaklaşımda derlenmiş olan uzantıların önceki birlikte çalışma derlemesini kullanarak Visual Studio eski sürümleriyle uyumlu olmadığı anlamına gelir.

bu, uzantınızı Visual Studio 2022 ' ye daha kolay bir şekilde güncellemeyi sağlayacak çok önemli avantajlara sahiptir:

- Bozuk API 'Ler, bulmayı ve düzeltmesini kolaylaştıran derleme zamanı hataları haline gelir.
- yalnızca Visual Studio 2022 ' de bozulmuş bir apı kullanan kodu güncelleştirmeniz gerekir.
- Eski, şimdi bozulmuş API 'yi yanlışlıkla kullanamazsınız.

genel olarak, bu değişiklikler tüm kullanıcılar için Visual Studio daha kararlı bir sürümüne neden olur. bu yaklaşımın önemli sakıncası, yönetilen derlemelerinizin her bir hedef Visual Studio sürümü için kodunuzu bir kez derlemeden hem Visual Studio 2019 hem de 2022 Visual Studio her ikisinde de çalıştıramayacak olması olabilir.

Visual Studio 2019 ve Visual Studio 2022 arasındaki apı farklılıkları nedeniyle derleme hatalarıyla çalışırken, bu işlemi nasıl giderebileceğine ilişkin yönergeler ile aşağıda listelenen apı veya kalıbı bulabilirsiniz.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` veya `uint` nerede `IntPtr` bekleniyor

Bunun çok yaygın bir hata olacağını bekliyoruz. Visual Studio 2022 ' i 64 bit işlem yapmak için, birlikte çalışma apı 'lerimizin bir işaretçisinin bir işaretçinin bir işaretçi boyutu değeri kullanması için 32-bit tamsayıya sığdırıldığı durumlarda düzeltilmesi gerekiyordu.

Örnek hata:

> Bağımsız değişken 3: ' Out uint ' değerinden ' Out System. IntPtr ' türüne dönüştürülemez

Kodunuzu yalnızca `IntPtr` `UIntPtr` `int` `uint` , kesmeyi çözümlemek için gereken veya sağlanacak şekilde güncelleştirmeniz yeterlidir.

Örnek düzelme:

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>İki derlemede tanımlanmış bir birlikte çalışma türü

C# derleyicisi, kullanmakta olduğunuz bir türün iki derlemede tanımlandığından bir hata bildirdiğinde, büyük olasılıkla SDK 'nın Visual Studio 2019 sürümünden bir derlemeye başvuruyorsunuzdur ve artık başvurmamalıdır.

Örnek hata:

> hata CS0433: ' IVsDpiAware ' türü hem ' Microsoft. VisualStudio. Interop, Version = 17.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' hem de ' Microsoft. VisualStudio. Shell. Interop. 16.0. DesignTime, Version = 16.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' içinde bulunur

hangi derleme adının Visual Studio 2022 ' de tercih edilen ad olduğunu görmek için [başvuru derleme yeniden eşleme tablosu](migrated-assemblies.md) ' na bakın.
Yukarıdaki örnek hatada adlı iki derlemeyi göz önünde bulundurarak ve bu tabloya baktığınızda, `Microsoft.VisualStudio.Interop` Yeni derleme adı olduğuna dikkat edin. Bu durumda, başvuruyu projeden kaldırmak daha sonra olur `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` .

bazı durumlarda, tür ileticileri içeren kullanımdan kaldırılan derleme için Visual Studio 2022 sürümlü bir paket sunuyoruz. bu kullanılabilir olduğunda, paket başvurunuz ' ı kaldırmak yerine Visual Studio 2022 sürümüne *yükseltme* seçeneğiniz vardır. Tür ileticileri, derleyicisinden hatayı çözmeyecektir.

Bazen bu başvuruların geçişli paket başvurusuyla gelebileceğini ve bu nedenle proje dosyanızda doğrudan bir başvuruya göre kaldırılması zor olabileceğini göz önünde bulundurun. bu gibi durumlarda, tüm doğrudan paketlerinizin Visual Studio 2022 SDK paketinin kendisini kullandığını doğrulayın. Kullanım dışı olan derlemede durmaktan sorumlu paketlerin zincirini belirlemek için *project.assets.jsüzerine* başvurabilirsiniz. Visual Studio 2022 sürümüne geçişli bir paket başvurusunu güncelleştirmek, doğrudan başvuru olarak yüklemek kadar kolaydır.

bağımlılık ağacını değiştiremediğiniz takdirde (örneğin, üçüncü taraf bağımlılığı içerdiğinden), ön Visual Studio 2022 paketine doğrudan bir paket başvurusu ekleyebilir ve `ExcludeAssets="compile"` `PackageReference` derleyici hatasını çözümlemek için bu öğeye meta veriler ekleyebilirsiniz. ancak bu tekniğin, uzantınızın bir ön Visual Studio 2022 derlemesinde bir bağımlılığı koruyabilir olduğunu ve uzantınızın çalışma zamanında hatalı durumda olabileceğini unutmayın.

### <a name="missing-reference-to-an-interop-assembly"></a>Birlikte çalışabilirlik derlemesine başvuru eksik

pre-Visual Studio 2022 SDK 'sına karşı derlenen bir derlemeye başvuru yaptığınızda bir derleme başvurusu eksik olduğunda bir hata alabilirsiniz.

Örnek hata:

> Hata CS0012 ' ıvstestextviewfilter ' türü başvurulmayan bir derlemede tanımlandı. ' Microsoft. VisualStudio. TextManager. Interop, version = 7.1.40304.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' derlemesine bir başvuru eklemeniz gerekir

[Başvuru derleme yeniden eşleme tablosunu](migrated-assemblies.md)kullanarak, istenen derlemenin gerçekten bir başvuru yapmanız gerektiğini doğrulayabilirsiniz.

en iyi çözüm, kaldırılan birlikte çalışma derlemesinin artık derleyici tarafından istenmemesi için Visual Studio 2022 SDK 'sına karşı derlenen bir sürüme yönelik bağımlılığının güncelleştirilmesi olur.

bazı durumlarda, tür ileticileri içeren kullanımdan kaldırılan derleme için Visual Studio 2022 sürümlü bir paket sunuyoruz. bu kullanılabilir olduğunda, tür ileticileri derleyicinin hatayı çözümleyecek şekilde kullanılmayan paketin Visual Studio 2022 sürümüne bir paket başvurusu ekleme seçeneğiniz vardır.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` eksik

İki ad alanında bu arabirimin iki tanımı vardır. Bunlardan yalnızca biri yönetilen tüketimine yöneliktir.

Visual Studio 2019 ad alanı | Visual Studio 2022 ad alanı | Amaçlanan kullanım
--|--|--
Microsoft. VisualStudio. Shell. ıasyncserviceprovider | Microsoft. VisualStudio. Shell. ıasyncserviceprovider | Yönetilen kod tüketimi
Microsoft. VisualStudio. Shell. Interop. ıasyncserviceprovider | Microsoft. VisualStudio. Shell. COMAsyncServiceProvider. ıasyncserviceprovider | yalnızca alt düzey birlikte çalışma

Hakkında bir hata görürseniz `IAsyncServiceProvider` , yerel kod (  ikinci satır) için tasarlanan birini kullanıyor olabilirsiniz.
Bu durumda, yeni ad alanına güncelleştirebilir veya daha yönetilen, daha kolay arabirimine geçiş yapabilirsiniz.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` ve `_DTE` tür dönüştürme başarısızlığı

`DTE` ve `_DTE` her ikisi de arayüzlerdir. Diğeri diğerini türetir. ancak Visual Studio 2022 ' de, temel ve türetilmiş türler değiştirilir.
Bu, belirli tür atamaları veya yayınları başarısız olur.

Bu Ayrıca, ' yi kullanmak için kullandığınız `new DTE()` , artık kullanmanız gereken anlamına gelir `new _DTE()` .

Bu sorunun çoğunu azaltmak için `DTE2` `EnvDTE80` bunun yerine ad alanından kullanın.

### <a name="missing-argument-on-a-method-invocation"></a>Yöntem çağrısında bağımsız değişken eksik

Artık, birlikte çalışma API 'sindeki isteğe bağlı parametreler için varsayılan bağımsız değişkenler bildirmemelidir.
bir COM birlikte çalışma çağrısının eksik bağımsız değişkeniyle ilgili bir hata alırsanız ve parametresi bir tür için çağrı yaparsanız `object` , Visual Studio 2019 birlikte çalışma apı 'sinin tanımladığı önceki varsayılan değer, `""` `""` derleme hatasını çözmek için bağımsız değişken olarak eklemeyi düşünün.

varsayılan bağımsız değişkenin ne olduğu hakkında şüpheli olduğunda, dil hizmeti bağlamını Visual Studio 2022 ' dan Visual Studio 2019 ' e geçmeyi deneyin, böylece varsayılan bağımsız değişkenin ne olduğunu görmek için daha eski birlikte çalışma derlemeleriyle ıntellisense 'i alın ve sonra kodu doğrudan kodunuza ekleyin. Visual Studio 2019 için derlendiğinde sorunsuz çalışmaya devam edecektir, ancak artık Visual Studio 2022 için derler.

Örnek düzelme:

```diff
-process4.Attach2();
+process4.Attach2("");
```
