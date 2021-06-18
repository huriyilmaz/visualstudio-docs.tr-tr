---
title: Visual Studio 2022 Preview'da YENI API değişiklikleri
description: Uzantıları 2022 Preview sürümüne değiştirirken mevcut VS uzantılarını derlemenin başarısız Visual Studio API değişiklikleri hakkında bilgi edinin.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308793"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Visual Studio 2022'de YENI API değişiklikleri

[!INCLUDE [preview-note](../includes/preview-note.md)]

Uzantıyı 2022'ye Visual Studio, burada listelenen yeni değişiklikler sizi etkileyebilir.

## <a name="reference-assemblies-no-longer-installed"></a>Başvuru derlemeleri artık yüklü değil

Bir derleme yükleme dizininden çözümlenen MSBuild'e başvurarak Visual Studio derlemelerin çoğu artık yüklenmemiş olabilir. NuGet kullanarak ihtiyacınız olan Visual Studio SDK başvuru derlemelerini edinmeniz gerekir. Bunu [yapma hakkında ayrıntılı adımlar](update-visual-studio-extension.md#modernize-your-vsix-project) için bkz. Projeleri modernleştirme.

## <a name="removed-apis"></a>API'ler kaldırıldı

Bu Visual Studio 2022'de, sonraki adımlarda bir dizi API Visual Studio kaldırılmıştır. Kaldırılan API'lerin listesi Kaldırılan [API Listesi sayfasında](removed-api-list.md) bulunabilir.

## <a name="interop-breaking-changes"></a>Birlikte çalışmaya neden olan değişiklikler

API'lerimizin çoğu 2022'Visual Studio değişti. Bu değişiklikler genellikle kodunuzun uygun olması için oldukça kolaydır.

Yeni değişiklikleri yönetmek için birlikte çalışma derlemelerinin dağıtımına yeni bir mekanizma sağlamayı planlıyoruz. Özellikle, 2022 ve Visual Studio için birçok ortak ortak çalışma arabiriminin tanımları ile tek bir birlikte çalışma derlemesi Visual Studio sağlaruz. Bu derleme, birden çok birlikte çalışma derlemeden Visual Studio arabirimleri için yönetilen tanımlar içerir. Yeni birlikte çalışma derlemesi `Microsoft.VisualStudio.Interop` NuGet paketi aracılığıyla dağıtılır.

Ancak, Visual Studio olarak yerel bağlamlarda kullanılan ve az sayıda hataya neden olan değişikliklere sahip olan tüm bileşenler kendi birlikte çalışma derlemelerine sahip olmaya devam eder (örneğin, hata ayıklayıcı derlemesi VisualStudio.Debugger.Interop.dll olarak kabul edilecektir). Her durumda derlemelere, tıpkı bugün olduğu gibi uygulamanıza başvurabilirsiniz.

Bu önemli bir değişikliktir ve bu yeni yaklaşımda yerleşik olarak API'leri ve derlemeyi kullanan uzantıların önceki birlikte çalışma derlemesini kullanan Visual Studio eski sürümleriyle uyumlu olmadığını ifade ediyor.

Bu, uzantınızı 2022'ye güncelleştirmenizi kolaylaştıracak birkaç Visual Studio sahiptir:

- Bozuk TÜM API'ler derleme zamanı hataları haline gelecek ve bulmaları ve düzeltmeleri kolaylaşır.
- Yalnızca 2022'de bozuk bir API kullanan Visual Studio gerekir.
- Eski ve bozuk API'yi yanlışlıkla kullanamayacaksınız.

Genel olarak, bu değişiklikler tüm kullanıcılar için daha kararlı bir Visual Studio sürümüne neden olur. Bu yaklaşımın en büyük dezavantajı, yönetilen derlemelerin her hedef sürüm için kodunuzu bir kez derlemeden hem Visual Studio 2019 hem de Visual Studio 2022'de Visual Studio olmasıdır.

Visual Studio 2019 ile Visual Studio 2022 arasındaki API farkları nedeniyle derleme hatalarında ilerlerken, nasıl düzelteceğime ilişkin kılavuzla aşağıda listelenmiş olan API'yi veya deseni bulabilirsiniz.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` veya `uint` nerede `IntPtr` beklendiği

Bunun çok yaygın bir hata olmasını bekliyoruz. 2022'de Visual Studio 64 bitlik bir işlem yapmak için, birlikte çalışma API'lerimizin bazılarının işaretçinin aslında işaretçi boyutlu bir değer kullanmak üzere 32 bit tamsayıya sığacak şekilde sığacak şekilde sabit olması gerekirdi.

Örnek hata:

> Bağımsız değişken 3: 'out uint' olan 'out System.IntPtr' değerine dönüştürülebildi

Tek yapmanız gereken kodunuzu, kesme sorununu çözmek için bekecek ya da sağlayacak ya da `IntPtr` nerede ya da daha önce kullanılacak şekilde `UIntPtr` `int` `uint` güncelleştirin.

Örnek düzeltme:

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>İki derlemede tanımlanan bir birlikte çalışma türü

C# derleyicisi, kullanmakta olduğunu bir türün iki derlemede tanımlandığına ilişkin bir hata raporlasa, büyük olasılıkla sdk'nın Visual Studio 2019 sürümünden artık başvurulamanız gereken bir derlemeye başvurabilirsiniz.

Örnek hata:

> hata CS0433: 'IVsDpiAware' türü hem 'Microsoft.VisualStudio.Interop' içinde var, Version=17.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' ve 'Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

2022'de [hangi](migrated-assemblies.md) derleme adının tercih edilen ad olduğunu görmek için başvuru derlemesi yeniden Visual Studio bakın.
Yukarıdaki örnek hatada adlı iki derlemeyi göz önünde bulundurarak ve bu tabloya bakarak, yeni `Microsoft.VisualStudio.Interop` derlemenin adı olduğunu fark edersiniz. Daha sonra düzeltme, başvurularını `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` projeden kaldırmaktır.

Bazı durumlarda, tür ileticileri Visual Studio kullanım dışı derleme için 2022 sürümüne sahip bir paket sunuyoruz. Bu kullanılabilir olduğunda, paketinizin  başvurularını kaldırmak yerine Visual Studio 2022 sürümüne yükseltme seçeneğiniz vardır. Tür ileticileri, derleyiciden hatayı çözer.

Bu başvuruların bazen geçişli paket başvurusuyla geleblir ve bu nedenle kaldırmanın proje dosyanıza yapılan doğrudan başvurudan daha zor olacağını unutmayın. Bu gibi durumlarda, tüm doğrudan paket başvurularının 2022 SDK Visual Studio olduğundan emin olun. Kullanım dışı *project.assets.jsgetirmekle* sorumlu paket zincirini belirlemek için aşağıdakilere başvurabilirsiniz. Geçişli paket başvurularını Visual Studio 2022 sürümüne güncelleştirmek, doğrudan başvuru olarak yüklemek kadar kolaydır.

Bağımlılık ağacını değiştiremiyorsanız (örneğin, bir üçüncü taraf bağımlılığı içerdiği için), derleyici hatasını çözmek için ön Visual Studio 2022 paketine doğrudan paket başvurusu ekleyebilir ve bu öğeye meta veriler `ExcludeAssets="compile"` `PackageReference` ebilirsiniz. Ancak bu teknikle, uzantınız 2022 öncesi derlemeye bağımlılığı Visual Studio ve uzantınız çalışma zamanında arızalanmış olabilir.

### <a name="missing-reference-to-an-interop-assembly"></a>Birlikte çalışma derlemesi başvurusu eksik

2022 SDK'sı ön Visual Studio derlenmiş bir derlemeye başvursanız, bir derleme başvurusu eksik hatası alabilirsiniz.

Örnek hata:

> Hata CS0012 'IVsTextViewFilter' türü başvurulmemiş bir derlemede tanımlanmıştır. 'Microsoft.VisualStudio.TextManager.Interop, Version=7.1.40304.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' derlemesi için bir başvuru eklemeniz gerekir

Başvuru [derlemesi yeniden kırpma tablosu kullanarak,](migrated-assemblies.md)istenen derlemenin aslında başvuracak bir derleme olmadığını onaylayın.

En iyi düzeltme, bağımlılığınızı Visual Studio 2022 SDK'sı ile derlenmiş bir sürüme güncelleştirmektir, böylece kaldırılan birlikte çalışma derlemesi artık derleyici tarafından istenmeyecektir.

Bazı durumlarda, tür ileticileri Visual Studio kullanım dışı derleme için 2022 sürümüne sahip bir paket sunuyoruz. Bu kullanılabilir olduğunda, tür ileticilerinin hatayı derleyiciden çözümlemesi için eski paketin Visual Studio 2022 sürümüne paket başvurusu ekleme seçeneğiniz vardır.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` eksik

Bu arabirimin iki tanımı vardır: iki ad alanı. Bunlardan yalnızca biri yönetilen tüketime yöneliktir.

Visual Studio 2019 Ad Alanı | Visual Studio 2022 Ad Alanı | Hedeflenen kullanım
--|--|--
Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Yönetilen kod tüketimi
Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.COMAsyncServiceProvider.IAsyncServiceProvider | yalnızca düşük düzey birlikte çalışma

hakkında bir hata `IAsyncServiceProvider` görüyorsanız, *yerel* kod (ikinci satır) için amaçlananı kullanıyor olabilirsiniz.
Öyleyse, yeni ad alanına güncelleştirebilirsiniz veya daha kolay yönetilen arabirime geçebilirsiniz.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` ve `_DTE` tür tür türlerini türe tür türe

`DTE` ve `_DTE` her ikisi de arabirimdir. Biri diğer taraftan türetildi. Ancak Visual Studio 2022'de temel ve türetilmiş türler değiştirildi.
Bu, belirli tür atamalarını veya atamalarını başarısız yapar.

Bu aynı zamanda, kullanmak için kullanılan yerde `new DTE()` artık kullanmak zorunda olduğu anlamına `new _DTE()` gelir.

### <a name="missing-argument-on-a-method-invocation"></a>Yöntem çağırmada bağımsız değişken eksik

Birkaç yöntem artık birlikte çalışma API'sinde isteğe bağlı parametreler için varsayılan bağımsız değişkenleri bildirmeyecek.
COM birlikte çalışma çağrısı için eksik bağımsız değişkenle ilgili bir hata alırsanız ve parametre bir tür için çağrırsa, Visual Studio 2019 birlikte çalışma API'sini tanımlandığı önceki varsayılan değer olabilir, bu nedenle derleme hatasını çözmek için bağımsız değişkeniniz olarak eklemeyi `object` `""` `""` düşünün.

Varsayılan bağımsız değişkenin ne olduğu konusunda şüpheniz varsa dil hizmeti bağlamınızı Visual Studio 2022'den Visual Studio 2019'a geçmeyi deneyin. Böylece, varsayılan bağımsız değişkenin ne olduğunu görmek için eski birlikte çalışma derlemeleriyle Intellisense'i edinebilirsiniz ve ardından kodunuzda açıkça ekleyin. Visual Studio 2019 için derlenmiş olduğunda iyi çalışmaya devam eder, ancak şimdi 2022 için Visual Studio derler.

Örnek düzeltme:

```diff
-process4.Attach2();
+process4.Attach2("");
```
