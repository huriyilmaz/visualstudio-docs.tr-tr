---
title: NuGet kullanarak TypeScript kodu derleme ve derleme
description: NuGet paketini kullanarak Visual Studio projelerinize Typescript desteğinin nasıl ekleneceğini öğrenin.
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
ms.openlocfilehash: b18f7503dd090856b48b6b6fa17af7af34886706
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980741"
---
# <a name="compile-typescript-code-aspnet-core"></a>TypeScript kodunu derle (ASP.NET Core)

Visual Studio yükleyicisindeki veya NuGet paketini kullanarak varsayılan olarak bulunan TypeScript SDK kullanarak projelerinize TypeScript desteği ekleyebilirsiniz. Visual Studio 2019 ' de geliştirilen projeler için, farklı platformlar ve ortamlarda daha fazla taşınabilirlik için TypeScript NuGet kullanmanızı öneririz.

ASP.NET Core projeleri için, NuGet paketi için yaygın olarak kullanılan bir kullanım, .NET Core CLI kullanarak TypeScript 'i derlemeye yöneliktir. proje dosyanızı TypeScript SDK yüklemesinden derleme hedeflerini içeri aktarmak üzere el ile düzenlemediğiniz sürece, NuGet paketi, ve gibi .NET Core CLI komutlarını kullanarak TypeScript derlemesini etkinleştirmenin tek yoludur `dotnet build` `dotnet publish` . ayrıca, ASP.NET Core ve TypeScript ile [MSBuild tümleştirme](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) için npm paketi üzerinden NuGet paketini seçin.

## <a name="add-typescript-support-with-nuget"></a>NuGet ile TypeScript desteği ekleme

[typescript NuGet paketi](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) typescript desteği ekler. typescript 3,2 veya üzeri için NuGet paketi projenize yüklendiğinde, typescript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.

Visual Studio yüklüyse, onunla birlikte gelen node.exe, Visual Studio tarafından otomatik olarak alınır. Yüklü Node.js yoksa, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

1. ASP.NET Core projenizi Visual Studio açın.

1. Çözüm Gezgini (sağ bölme). proje düğümüne sağ tıklayın ve **NuGet paketlerini yönet**' i seçin. **araştır** sekmesinde, **Microsoft. TypeScript. MSBuild** araması yapın ve ardından **paketi yüklemek için sağdaki aç '** a tıklayın.

   ![NuGet paketi ekle](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio, NuGet paketini Çözüm Gezgini **bağımlılıklar** düğümü altına ekler. Aşağıdaki paket başvurusu *. csproj dosyanıza eklenir.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Proje düğümüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TYPESCRIPT JSON yapılandırma dosyasını** seçin ve ardından **Ekle**' ye tıklayın.

   Visual Studio dosya *tsconfig.js* proje köküne ekler. TypeScript derleyicisi [seçeneklerini yapılandırmak](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) için bu dosyayı kullanabilirsiniz.

1. İstediğiniz derleyici seçeneklerini ayarlamak için *tsconfig.json* ve Update ' i açın.

   Aşağıda bir basit *tsconfig.js* dosyası örneği verilmiştir.

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
   - *Include* , derleyiciye TypeScript (*. TS) dosyalarını nerede bulacağını söyler.
   - *OutDir* seçeneği, TypeScript derleyicisi tarafından transpiled olan düz JavaScript dosyaları için çıkış klasörünü belirtir.
   - *sourcemap* seçeneği derleyicinin *sourcemap* dosyaları oluşturup oluşturmayacağını belirtir.

   Önceki yapılandırma TypeScript 'i yapılandırmaya yönelik temel bir giriş sağlar. Diğer seçeneklerle ilgili daha fazla bilgi için bkz. [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

### <a name="build-the-application"></a>Uygulama oluşturma

1. Projenize TypeScript (*. TS*) veya TypeScript JSX (*. TSX*) dosyaları ekleyin ve ardından TypeScript kodu ekleyin. TypeScript 'in basit bir örneği için aşağıdakileri kullanın:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. SDK olmayan eski bir stil projesi kullanıyorsanız, derlemeden önce [varsayılan içeri aktarmaları kaldır](#remove-default-imports) ' daki yönergeleri izleyin.

1. **Build > Build Solution** öğesini seçin.

   Uygulamayı çalıştırdığınızda otomatik olarak oluştursa da, yapı işlemi sırasında gerçekleşen bir şeye göz atmak istiyoruz:

   Kaynak haritaları oluşturduysanız, *OutDir* seçeneğinde belirtilen klasörü açın ve oluşturulan * js. map dosyaları ile birlikte oluşturulan * .js dosyalarını bulabilirsiniz.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

1. Projeyi her kaydedişinizde derlemek istiyorsanız *. tsconfig içindeki *Compileonsave* seçeneğini kullanın.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

uygulamanızı derlemek için görev çalıştırıcısı ile gulp kullanma örneği için bkz. [ASP.NET Core ve TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Visual Studio, Node.js bir sürümü ya da beklediğiniz sürümden farklı bir üçüncü taraf aracı kullanıyorsa sorunlarla karşılaşırsanız Visual Studio için yolunu ayarlamanız gerekebilir. **Araçlar**  >  **seçeneklerini** belirleyin. **Projeler ve çözümler** altında **Web paket yönetimi**  >  **dış Web araçları**' nı seçin.

### <a name="run-the-application"></a>Uygulamayı çalıştırma

Derlemeden sonra uygulamayı çalıştırma yönergeleri için, bkz. [ilk Node.js uygulamanızı oluşturma](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application).

### <a name="nuget-package-structure-details"></a>NuGet paket yapısı ayrıntıları

`Microsoft.TypeScript.MSBuild.nupkg` iki ana klasör içerir:

- *derleme* klasörü

    Bu klasörde iki dosya bulunur.
    Hem giriş noktaları hem de ana TypeScript hedef dosyası ve props dosyası için sırasıyla.

    1. *Microsoft. TypeScript. MSBuild. targets*

        Bu dosya, *Araçlar* klasöründen *Microsoft. TypeScript. targets* almadan önce *TypeScript.Tasks.dll* yolu gibi çalışma zamanı platformunu belirten değişkenleri ayarlar.

    2. *Microsoft. TypeScript. MSBuild. props*

        Bu dosya, *Araçlar* klasöründen *Microsoft. TypeScript. default. props* içeri aktarır ve derleme NuGet aracılığıyla başlatıldığını gösteren özellikleri ayarlar.

- *Araçlar* klasörü

    2,3 ' den önceki paket sürümleri yalnızca bir TSC klasörü içerir. *Microsoft. TypeScript. targets* ve *TypeScript.Tasks.dll* kök düzeyinde bulunur.

    Paket sürümleri 2,3 ve üzeri sürümlerde kök düzeyi `Microsoft.TypeScript.targets` ve içerir `Microsoft.TypeScript.Default.props` . bu dosyalar hakkında daha fazla bilgi için bkz. [MSBuild Configuration](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Ayrıca, klasör üç alt klasör içerir:

    1. *net45*

        Bu klasör `TypeScript.Tasks.dll` ve üzerinde bağımlı olduğu diğer dll 'leri içerir.
        Windows platformunda bir proje oluştururken, MSBuild dll 'leri bu klasörden kullanır.

    2. *Netstandard 1.3*

        bu klasör `TypeScript.Tasks.dll` , Windows olmayan bir makinede proje oluştururken kullanılan başka bir sürümünü içerir.

    3. *TSC*

        Bu klasör `tsc.js` `tsserver.js` ve bunları düğüm komut dosyaları olarak çalıştırmak için gereken tüm bağımlılık dosyalarını içerir.

        > [!NOTE]
        > Visual Studio yüklüyse, onunla paketlenmiş *node.exe* otomatik olarak alınır. Aksi takdirde Node.js makinede yüklü olmalıdır.

        3,1 ' den önceki sürümler `tsc.exe` , derlemeyi çalıştırmak için yürütülebilir bir dosya içeriyordu. Sürüm 3,1 ' de, bu, kullanımı Lehde kaldırılmıştır `node.exe` .

### <a name="remove-default-imports"></a>Varsayılan içeri aktarmaları kaldır

[SDK olmayan biçim biçimini](/nuget/resources/check-project-format)kullanan daha eski ASP.NET Core projelerde, bazı proje dosyası öğelerini kaldırmanız gerekebilir.

bir proje için MSBuild desteği için NuGet paketini kullanıyorsanız, proje dosyası veya içeri aktarmamalıdır `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets` . dosyalar NuGet paketi tarafından içeri aktarıldığından, bunların ayrı olarak dahil edilmesi istenmeden davranışa neden olabilir.

1. Projeye sağ tıklayın ve **Project kaldır**' ı seçin.

1. Projeye sağ tıklayın ve **Düzenle \<*project file name*\>**' yi seçin.

   Proje dosyası açılır.

1. Ve başvurularını kaldırın `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets` .

   Kaldırılacak içeri aktarmalar aşağıdakine benzer şekilde görünür:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
