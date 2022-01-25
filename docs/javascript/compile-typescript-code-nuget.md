---
title: NuGet kullanarak TypeScript kodu derleme ve derleme
description: NuGet paketini kullanarak Visual Studio projelerinize TypeScript desteği NuGet öğrenin.
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
ms.openlocfilehash: 85a61466bb60a9b0c1883daa754b963044519331
ms.sourcegitcommit: 429b2378ee21b5f473b26f4b4ea0a70372a34ec2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "137733407"
---
# <a name="compile-typescript-code-aspnet-core"></a>TypeScript kodunu derleme (ASP.NET Core)

TypeScript SDK yükleyicisinde varsayılan olarak kullanılabilir olan Visual Studio paketi kullanarak projelerinize TypeScript desteği NuGet abilirsiniz. Visual Studio 2019'da geliştirilen projeler için, farklı platformlar ve ortamlar arasında daha fazla taşınabilirlik için TypeScript NuGet'i kullanmalarını teşvik ederiz.

Daha ASP.NET Core projelerde, NuGet paketi için yaygın kullanımlardan biri, .NET Core CLI. Proje dosyanızı bir TypeScript SDK yüklemesinde derleme hedeflerini içeri aktaracak şekilde el ile düzenlemedikçe, NuGet paketi ve gibi .NET Core CLI komutları kullanarak TypeScript derlemesini etkinleştirmenin tek `dotnet build` yolu `dotnet publish` olur. Ayrıca, [MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) typescript ASP.NET Core için npm paketi NuGet paketi seçin.

## <a name="add-typescript-support-with-nuget"></a>NuGet ile TypeScript desteği ekleme

[TypeScript NuGet paketi,](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) TypeScript desteği ekler. Projenize TypeScript 3.2 veya NuGet paketi yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.

Bir Visual Studio yüklüyse, node.exe paketle birlikte gelen paket otomatik olarak Visual Studio. Yüklü bir Node.js, lts sürümünüNode.jsweb [ sitesinden yüklemenizi ](https://nodejs.org/en/download/) öneririz.

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

   Visual Studio *tsconfig.json dosyasını* proje köküne ekler. TypeScript derleyicisi seçeneklerini [yapılandırmak için](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) bu dosyayı kullanabilirsiniz.

1. *tsconfig.json'ı* açın ve istediğiniz derleyici seçeneklerini ayarlamak için güncelleştirin.

   Aşağıda basit bir *tsconfig.json dosyası örneği ve* ardından ve bir örnek ve ardından yer almaktadır.

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

   Önceki yapılandırma, TypeScript'i yapılandırmaya yalnızca temel bir giriş sağlar. Diğer seçenekler hakkında bilgi için bkz. [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

### <a name="build-the-application"></a>Uygulama oluşturma

1. Projenize TypeScript (*.ts*) veya TypeScript JSX (*.tsx*) dosyalarını ekleyin ve ardından TypeScript kodunu ekleyin. Basit bir TypeScript örneği için aşağıdakini kullanın:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. SDK olmayan daha eski bir stil projesi kullanıyorsanız, Varsayılan içeri aktarmaları yapılmadan [önce kaldırma yönergelerini](#remove-default-imports) izleyin.

1. Derleme **ve Derleme >'ı seçin.**

   Uygulamayı çalıştırarak otomatik olarak derlemeye devam ediyor olsa da, derleme işlemi sırasında olan bir şeye göz atacağız:

   Kaynak eşlemeleri oluşturduysanız *outDir* seçeneğinde belirtilen klasörü açın ve oluşturulan *.js dosyalarıyla birlikte oluşturulan *js.map dosyaları) bulursanız.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

1. Projeyi her kaydeden derlemek için *tsconfig.json'da* *compileOnSave* seçeneğini kullanın.

   ```json
   {
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Uygulamanızı derlemek için Görev Çalıştırıcısı ile gülep kullanma örneği için bkz. [ASP.NET Core TypeScript.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

Visual Studio'nin Node.js sürümünü veya beklenen sürümden farklı bir üçüncü taraf aracını kullanması ile ilgili sorunlaryla karşı karşınız varsa, Visual Studio için yolu ayarlamanız gerekir. Araçlar **Seçenekleri'ne**  >  **tıklayın.** Projeler **ve çözümler altında Web** Uygulaması Dış Web   >  **Paket Yönetimi'ı seçin.**

### <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı derledikten sonra çalıştırma yönergeleri için bkz. [İlk uygulama Node.js oluşturma.](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application)

### <a name="nuget-package-structure-details"></a>NuGet yapısı ayrıntıları

`Microsoft.TypeScript.MSBuild.nupkg` iki ana klasör içerir:

- *build* klasörü

    Bu klasörde iki dosya bulunur.
    Her ikisi de ana TypeScript hedef dosyası ve props dosyası için giriş noktalarıdır.

    1. *Microsoft.TypeScript. MSBuild.targets*

        Bu dosya, araçlar klasöründen *Microsoft.TypeScript.targets'i* içeri aktarmadan önce *TypeScript.Tasks.dll* yolu gibi çalışma zamanı platformunu belirten *değişkenleri* ayarlar.

    2. *Microsoft.TypeScript. MSBuild.props*

        Bu dosya, *araçlar klasöründen Microsoft.TypeScript.Default.props* dosyasını içeri aktarır ve derlemenin NuGet. 

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

Eski ASP.NET Core SDK stili [olmayan biçimi](/nuget/resources/check-project-format)kullanan projelerde bazı proje dosyası öğelerini kaldırmanız gerekebilir.

Bir proje için NuGet için MSBuild paketini kullanıyorsanız, proje dosyası veya 'ı içeri `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets` aktarmamalı. Dosyalar, ayrı olarak dahil NuGet paket tarafından içe aktarılır, bu nedenle, bu, kötü bir davranışa neden olabilir.

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
