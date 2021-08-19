---
title: NuGet kullanarak TypeScript kodu derleme ve derleme
description: NuGet paketini kullanarak Visual Studio projelerinize Typescript desteği NuGet öğrenin.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8e50a88b53683ba98a2633e9fa4adbab7111d2ca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077861"
---
# <a name="compile-typescript-code-aspnet-core"></a>TypeScript kodunu derleme (ASP.NET Core)

TypeScript SDK yükleyicisinde varsayılan olarak kullanılabilir veya Visual Studio paketi kullanarak projelerinize TypeScript desteği NuGet abilirsiniz. Visual Studio 2019'da geliştirilen projeler için, farklı platformlar ve ortamlar arasında daha NuGet için TypeScript NuGet'i kullanmalarını teşvik ederiz.

Daha ASP.NET Core projelerde, NuGet paketi için yaygın kullanımlardan biri, .NET Core CLI. Proje dosyanızı bir TypeScript SDK yüklemesinde derleme hedeflerini içeri aktaracak şekilde el ile düzenlemedikçe, ve gibi NuGet komutlarını kullanarak TypeScript derlemesini etkinleştirmenin tek yolu .NET Core CLI `dotnet build` `dotnet publish` paketidir. Ayrıca, [MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) ve TypeScript ile ASP.NET Core için npm paketi NuGet paketi seçin.

## <a name="add-typescript-support-with-nuget"></a>NuGet ile TypeScript desteği ekleme

[TypeScript NuGet paketi,](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) TypeScript desteği ekler. Projenize TypeScript 3.2 veya daha yeni bir NuGet paketi yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.

Bir Visual Studio yüklüyse, node.exe paketle birlikte gelen paket otomatik olarak Visual Studio. Yüklü bir Node.js, LTS sürümünüNode.js[ yüklemenizi ](https://nodejs.org/en/download/) öneririz.

1. ASP.NET Core projenizi Visual Studio.

1. Bölmede Çözüm Gezgini (sağ bölme). Proje düğümüne sağ tıklayın ve Paketleri **Yönet'NuGet seçin.** Gözat **sekmesinde** **Microsoft.TypeScript.MSBuild** araması yapın ve ardından paketi **yüklemek** için sağdan Yükle'ye tıklayın.

   ![Paket NuGet ekleme](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio paketi NuGet'daki **Bağımlılıklar** düğümü altına Çözüm Gezgini. Aşağıdaki paket başvurusu *.csproj dosyanıza eklenir.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Proje düğümüne sağ tıklayın ve Yeni **Öğe'> Ekle'yi seçin.** **TypeScript JSON Yapılandırma Dosyasını seçin ve** ekle'ye **tıklayın.**

   Visual Studio, *tsconfig.jsproje* köküne ekler. TypeScript derleyicisi seçeneklerini [yapılandırmak için](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) bu dosyayı kullanabilirsiniz.

1. Açık *tsconfig.jsaçın* ve güncelleştirin ve istediğiniz derleyici seçeneklerini ayarlayın.

   Aşağıda, dosyada basit birtsconfig.js *örneği ve* ardından ve bir örnek ve açıklama ve açıklama yer aleladedir.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Bu örnekte:
   - *include,* derleyiciye TypeScript (*.ts) dosyalarının nerede bulun olduğunu söyler.
   - *outDir* seçeneği, TypeScript derleyicisi tarafından transpile edilen düz JavaScript dosyalarının çıkış klasörünü belirtir.
   - *sourceMap* seçeneği, derleyicinin sourceMap dosyaları *oluşturıp oluşturmay olmadığını* gösterir.

   Önceki yapılandırma, TypeScript'i yapılandırmaya yalnızca temel bir giriş sağlar. Diğer seçenekler hakkında bilgi için [bkz.tsconfig.js.](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

### <a name="build-the-application"></a>Uygulama oluşturma

1. Projenize TypeScript (*.ts*) veya TypeScript JSX (*.tsx*) dosyalarını ekleyin ve ardından TypeScript kodunu ekleyin. Basit bir TypeScript örneği için aşağıdakini kullanın:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. SDK olmayan daha eski bir stil projesi kullanıyorsanız, Varsayılan içeri aktarmaları yapılmadan [önce kaldırma yönergelerini](#remove-default-imports) izleyin.

1. Build **> Build Solution (Derleme Çözümü) seçin.**

   Uygulamayı çalıştırarak otomatik olarak derlemeye devam ediyor olsa da, derleme işlemi sırasında olan bir şeye göz atacağız:

   Kaynak eşlemeleri oluşturduysanız *outDir* seçeneğinde belirtilen klasörü açın ve oluşturulan *.js dosyalarıyla birlikte oluşturulan *js.map dosyaları) bulursanız.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

1. Projeyi her kaydeden derlemek için *.tsconfig içinde *compileOnSave* seçeneğini kullanın.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Uygulamanızı derlemek için Görev Çalıştırıcısı ile gülep kullanma örneği için bkz. [ASP.NET Core TypeScript.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

Visual Studio'ın Node.js sürümünü veya beklenen sürümden farklı bir üçüncü taraf aracını kullanması ile ilgili sorunlaryla karşı karşınız varsa, Visual Studio'nin kullanabileceği yolu Visual Studio gerekir. Araçlar **Seçenekleri'ne**  >  **tıklayın.** Projeler **ve çözümler altında Web** Uygulaması Dış Web   >  **Paket Yönetimi'ı seçin.**

### <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı derledikten sonra çalıştırma yönergeleri için bkz. [İlk uygulamanızı Node.js oluşturma.](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application)

### <a name="nuget-package-structure-details"></a>NuGet yapısı ayrıntıları

`Microsoft.TypeScript.MSBuild.nupkg` iki ana klasör içerir:

- *build* klasörü

    Bu klasörde iki dosya bulunur.
    Her ikisi de ana TypeScript hedef dosyası ve props dosyası için giriş noktalarıdır.

    1. *Microsoft.TypeScript. MSBuild.targets*

        Bu dosya, araçlar klasöründen *Microsoft.TypeScript.targets'i* içeri *aktarmadan* önceTypeScript.Tasks.dllyolu gibi çalışma zamanı platformunu belirten *değişkenleri* ayarlar.

    2. *Microsoft.TypeScript. MSBuild.props*

        Bu dosya, *araçlar klasöründen Microsoft.TypeScript.Default.props* dosyasını içeri aktarıyor ve derlemenin NuGet. 

- *araçlar* klasörü

    2.3'den önceki paket sürümleri yalnızca bir tsc klasörü içerir. *Microsoft.TypeScript.targets* *TypeScript.Tasks.dll* kök düzeyinde bulunur.

    Paket 2.3 ve sonraki sürümlerinde kök düzeyi ve `Microsoft.TypeScript.targets` `Microsoft.TypeScript.Default.props` içerir. Bu dosyalar hakkında daha fazla bilgi için [bkz. MSBuild Yapılandırma.](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html)

    Ayrıca, klasör üç alt klasör içerir:

    1. *net45*

        Bu klasör ve `TypeScript.Tasks.dll` bağlı olduğu diğer URL'leri içerir.
        Windows platformunda proje MSBuild bu klasördeki URL'leri kullanır.

    2. *netstandard1.3*

        Bu klasör, sanal makine olmayan `TypeScript.Tasks.dll` bir makinede proje oluşturmada kullanılan başka bir Windows içerir.

    3. *Tsc*

        Bu klasör , `tsc.js` ve `tsserver.js` bunları düğüm betikleri olarak çalıştırmak için gereken tüm bağımlılık dosyalarını içerir.

        > [!NOTE]
        > Bir Visual Studio yüklüyse, *node.exe* paketle birlikte otomatik olarak yüklenir. Aksi Node.js makineye yüklenmiş olması gerekir.

        3.1'den önceki sürümlerde derlemeyi `tsc.exe` çalıştırmak için yürütülebilir dosya bulunuyor. Sürüm 3.1'de bu, kullanılarak `node.exe` kaldırılmıştır.

### <a name="remove-default-imports"></a>Varsayılan içeri aktarmaları kaldırma

Eski ASP.NET Core SDK stili olmayan [biçimi](https://docs.microsoft.com/nuget/resources/check-project-format)kullanan projelerde bazı proje dosyası öğelerini kaldırmanız gerekebilir.

Bir proje için NuGet için MSBuild paketini kullanıyorsanız, proje dosyası veya 'ı içeri `Microsoft.TypeScript.Default.props` aktarmamalı. `Microsoft.TypeScript.targets` Dosyalar, paket tarafından NuGet, bu nedenle ayrı olarak dahil edilirler, bu da kötü bir davranışa neden olabilir.

1. Projeye sağ tıklayın ve Yüklemeden **kaldır'ı Project.**

1. Projeye sağ tıklayın ve Düzenle'yi **seçin. \<*project file name*\>**

   Proje dosyası açılır.

1. ve başvurularını `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets` kaldırın.

   Kaldır için içeri aktarmalar aşağıdakine benzer:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
