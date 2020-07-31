---
title: NuGet kullanarak TypeScript kodu derleme ve derleme
description: Visual Studio 'da TypeScript 'i derlemeyi ve derlemeyi öğrenin.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ac917248915129b8d93dc776ac7d35a2ed227069
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87454603"
---
# <a name="compile-typescript-code-aspnet-core"></a>TypeScript kodunu derle (ASP.NET Core)

Visual Studio yükleyicisindeki varsayılan olarak veya NuGet paketini kullanarak TypeScript SDK kullanarak projelerinize TypeScript desteği ekleyebilirsiniz. Visual Studio 2019 ' de geliştirilen projeler için, farklı platformlar ve ortamlarda daha fazla taşınabilirlik için TypeScript NuGet 'i kullanmanızı öneririz.

ASP.NET Core projeler için, NuGet paketi için yaygın olarak kullanılan bir kullanım, .NET Core CLI kullanılarak TypeScript 'i derlemek içindir. Proje dosyanızı TypeScript SDK yüklemesinden derleme hedeflerini içeri aktarmak üzere el ile düzenlemediğiniz sürece, ve gibi .NET Core CLI komutlarını kullanarak TypeScript derlemesini etkinleştirmenin tek yolu NuGet paketidir `dotnet build` `dotnet publish` . Ayrıca, ASP.NET Core ve TypeScript ile [MSBuild tümleştirmesi](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) için NPM paketi üzerinden NuGet paketini seçin.

## <a name="add-typescript-support-with-nuget"></a>NuGet ile TypeScript desteği ekleme

[TypeScript NuGet paketi](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) TypeScript desteği ekler. TypeScript 3,2 veya üzeri için NuGet paketi projenize yüklendiğinde, TypeScript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.

Visual Studio yüklüyse, onunla paketlenmiş node.exe Visual Studio tarafından otomatik olarak alınır. Yüklü Node.js yoksa, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

1. ASP.NET Core projenizi Visual Studio 'da açın.

1. Çözüm Gezgini (sağ bölme). proje düğümüne sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. **Araştır** sekmesinde, **Microsoft. TypeScript. MSBuild**' i arayın ve ardından, paketi yüklemek için **sağdaki aç '** a tıklayın.

   ![NuGet paketi Ekle](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio, NuGet paketini Çözüm Gezgini içindeki **Bağımlılıklar** düğümüne ekler. Aşağıdaki paket başvurusu *. csproj dosyanıza eklenir.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Proje düğümüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TYPESCRIPT JSON yapılandırma dosyasını**seçin ve ardından **Ekle**' ye tıklayın.

   Visual Studio *tsconfig.js* dosyayı proje köküne ekler. TypeScript derleyicisi [seçeneklerini yapılandırmak](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) için bu dosyayı kullanabilirsiniz.

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

1. **Build > Build Solution**öğesini seçin.

   Uygulamayı çalıştırdığınızda otomatik olarak oluştursa da, yapı işlemi sırasında gerçekleşen bir şeye göz atmak istiyoruz:

   Kaynak haritaları oluşturduysanız, *OutDir* seçeneğinde belirtilen klasörü açın ve oluşturulan *. js dosyalarını, oluşturulan * js. map dosyaları ile birlikte bulabilirsiniz.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

1. Projeyi her kaydedişinizde derlemek istiyorsanız *. tsconfig içindeki *Compileonsave* seçeneğini kullanın.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Uygulamanızı derlemek için görev Çalıştırıcısı ile Gulp kullanma örneği için bkz. [ASP.NET Core ve TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Visual Studio 'nun Node.js bir sürümünü veya sizin beklediğiniz sürümden farklı bir üçüncü taraf aracını kullandığı sorunlarla karşılaşırsanız, Visual Studio 'nun yolunu kullanacak şekilde ayarlamanız gerekebilir. **Araçlar**  >  **seçeneklerini**belirleyin. **Projeler ve çözümler**altında **Web paket yönetimi**  >  **dış Web araçları**' nı seçin.

### <a name="nuget-package-structure-details"></a>NuGet paket yapısı ayrıntıları

`Microsoft.TypeScript.MSBuild.nupkg`iki ana klasör içerir:

- *derleme* klasörü

    Bu klasörde iki dosya bulunur.
    Hem giriş noktaları hem de ana TypeScript hedef dosyası ve props dosyası için sırasıyla.

    1. *Microsoft. TypeScript. MSBuild. targets*

        Bu dosya, *Araçlar* klasöründen *Microsoft. TypeScript. targets* almadan önce *TypeScript.Tasks.dll*yolu gibi çalışma zamanı platformunu belirten değişkenleri ayarlar.

    2. *Microsoft. TypeScript. MSBuild. props*

        Bu dosya, *Araçlar* klasöründen *Microsoft. TypeScript. default. props* Içeri aktarır ve yapılandırmanın NuGet aracılığıyla başlatıldığını gösteren özellikleri ayarlar.

- *Araçlar* klasörü

    2,3 ' den önceki paket sürümleri yalnızca bir TSC klasörü içerir. *Microsoft. TypeScript. targets* ve *TypeScript.Tasks.dll* kök düzeyinde bulunur.

    Paket sürümleri 2,3 ve üzeri sürümlerde kök düzeyi `Microsoft.TypeScript.targets` ve içerir `Microsoft.TypeScript.Default.props` . Bu dosyalar hakkında daha fazla bilgi için bkz. [MSBuild yapılandırması](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Ayrıca, klasör üç alt klasör içerir:

    1. *net45*

        Bu klasör `TypeScript.Tasks.dll` ve üzerinde bağımlı olduğu diğer dll 'leri içerir.
        Bir Windows platformunda bir proje oluştururken, MSBuild bu klasördeki dll 'Leri kullanır.

    2. *Netstandard 1.3*

        Bu klasör `TypeScript.Tasks.dll` , Windows dışı bir makinede proje oluştururken kullanılan başka bir sürümünü içerir.

    3. *TSC*

        Bu klasör `tsc.js` `tsserver.js` ve bunları düğüm komut dosyaları olarak çalıştırmak için gereken tüm bağımlılık dosyalarını içerir.

        > [!NOTE]
        > Visual Studio yüklüyse, bu, ile paketlenmiş *node.exe* otomatik olarak alınacaktır. Aksi takdirde Node.js makinede yüklü olmalıdır.

        3,1 ' den önceki sürümler `tsc.exe` , derlemeyi çalıştırmak için yürütülebilir bir dosya içeriyordu. Sürüm 3,1 ' de, bu, kullanımı Lehde kaldırılmıştır `node.exe` .

### <a name="remove-default-imports"></a>Varsayılan içeri aktarmaları kaldır

[SDK olmayan biçim biçimini](https://docs.microsoft.com/nuget/resources/check-project-format)kullanan daha eski ASP.NET Core projelerde, bazı proje dosyası öğelerini kaldırmanız gerekebilir.

Bir proje için MSBuild desteği için NuGet paketini kullanıyorsanız, proje dosyası veya içeri aktarmamalıdır `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets` . Dosyalar NuGet paketi tarafından içeri aktarıldığından, bunları ayrı olarak dahil etmek istenmeden davranışa neden olabilir.

1. Projeye sağ tıklayın ve **Projeyi Kaldır**' ı seçin.

1. Projeye sağ tıklayın ve **Düzenle \<*project file name*\> **' yi seçin.

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
