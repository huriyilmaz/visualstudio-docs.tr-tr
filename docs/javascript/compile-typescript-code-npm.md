---
title: NPM kullanarak TypeScript kodu derleme ve derleme
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
ms.openlocfilehash: add67535c0c3c9e4a48b95c2b9d5fe0717511797
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414387"
---
# <a name="compile-typescript-code-nodejs"></a>TypeScript kodunu derle (Node.js)

Visual Studio yükleyicisindeki veya NPM kullanarak varsayılan olarak bulunan TypeScript SDK kullanarak projelerinize TypeScript desteği ekleyebilirsiniz. Visual Studio 2019 ' de geliştirilen projeler için, farklı platformlar ve ortamlarda daha fazla taşınabilirlik sağlamak üzere TypeScript NPM paketini kullanmanızı öneririz.

ASP.NET Core projeleri için, bunun yerine [NuGet paketini](../javascript/compile-typescript-code-nuget.md) kullanmanız önerilir.

## <a name="add-typescript-support-using-npm"></a>NPM kullanarak TypeScript desteği ekleme

[TypeScript NPM paketi](https://www.npmjs.com/package/typescript) TypeScript desteği ekler. TypeScript 2,1 veya üzeri için NPM paketi projenize yüklendiğinde, TypeScript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.

1. Node.js geliştirme iş yükünü ve Node.js çalışma zamanını yüklemek için [yönergeleri izleyin](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) .

   Visual Studio ile en basit tümleştirme için, boş Node.js Web uygulaması şablonu gibi Node.js TypeScript şablonlarından birini kullanarak projenizi oluşturun. Aksi takdirde, Visual Studio ile birlikte gelen Node.js JavaScript şablonunu kullanın ve buradaki yönergeleri izleyin veya [açık bir klasör](../javascript/develop-javascript-code-without-solutions-projects.md) projesi kullanın.

1. Projeniz zaten içermiyorsa, [TypeScript NPM paketini](https://www.npmjs.com/package/typescript)yükledikten sonra.

   Çözüm Gezgini (sağ bölme) menüsünde, proje kökünde *package.js* açın. Listelenen paketler, Çözüm Gezgini NPM düğümü altındaki paketlere karşılık gelir. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](../javascript/npm-package-management.md).

   Node.js bir proje için, komut satırını veya IDE 'yi kullanarak TypeScript NPM paketini yükleyebilirsiniz. IDE kullanarak yüklemek için Çözüm Gezgini NPM düğümüne sağ tıklayın, **Yeni NPM paketi yüklensin** ' i seçin, **TypeScript** için arama yapın ve paketi yüklemek için.

   Paket yükleme ilerlemesini görmek için **Çıkış** penceresindeki **NPM** seçeneğini işaretleyin. Yüklü paket, Çözüm Gezgini **NPM** düğümünün altında görüntülenir.

1. Projeniz zaten içermiyorsa, proje köküne bir *. tsconfig* dosyası ekleyin. Dosyayı eklemek için, proje düğümüne sağ tıklayın ve **> yeni öğe Ekle** ' yi seçin. **TYPESCRIPT JSON yapılandırma dosyasını** seçin ve ardından **Ekle** ' ye tıklayın.

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
       "outDir": "dist"
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

## <a name="build-the-application"></a>Uygulama oluşturma

1. Projenize TypeScript ( *. TS* ) veya TypeScript JSX ( *. TSX* ) dosyaları ekleyin ve ardından TypeScript kodu ekleyin. TypeScript 'in basit bir örneği için aşağıdakileri kullanın:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. *package.js* , aşağıdaki komut dosyalarını kullanarak Visual Studio Build ve Clean komutları için destek ekleyin.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   WebPack gibi üçüncü taraf bir araç kullanarak derlemeniz gerekiyorsa, dosyanıza *package.js* bir komut satırı derleme betiği ekleyebilirsiniz:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   WebPack 'i tepki verme ve bir WebPack yapılandırma dosyası ile kullanma örneği için bkz. [Node.js bir Web uygulaması oluşturma ve tepki](../javascript/tutorial-nodejs-with-react-and-jsx.md)verme.

   TypeScript ile Vue.js kullanmayla ilgili bir örnek için bkz. [Vue.js uygulaması oluşturma](/javascript/create-application-with-vuejs).

1. Başlangıç sayfası, Node.js çalışma zamanı, uygulama bağlantı noktası veya çalışma zamanı bağımsız değişkenlerinin yolu gibi seçenekleri yapılandırmanız gerekirse, Çözüm Gezgini proje düğümüne sağ tıklayın ve **Özellikler** ' i seçin.

   >[!NOTE]
   > Üçüncü taraf araçları yapılandırırken Node.js projeler, **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **Web paket yönetimi**  >  **dış Web araçları** altında yapılandırılan yolları kullanmaz. Bu ayarlar diğer proje türleri için kullanılır.

1. **Build > Build Solution** öğesini seçin.

   Uygulamayı çalıştırdığınızda otomatik olarak oluştursa da, yapı işlemi sırasında gerçekleşen bir şeye göz atmak istiyoruz:

   Kaynak haritaları oluşturduysanız, *OutDir* seçeneğinde belirtilen klasörü açın ve oluşturulan \* . js dosyalarını oluşturulan \* js. map dosyaları ile birlikte bulabilirsiniz.

   [Hata ayıklama](../javascript/debug-nodejs.md)için kaynak eşleme dosyaları gereklidir.

### <a name="run-the-application"></a>Uygulamayı çalıştırma

Derlemeden sonra uygulamayı çalıştırma yönergeleri için, bkz. [ilk Node.js uygulamanızı oluşturma](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-application).

## <a name="automate-build-tasks"></a>Derleme görevlerini otomatikleştirin

NPM ve WebPack gibi üçüncü taraf araçlara yönelik görevleri otomatikleştirmeye yardımcı olması için, Visual Studio 'da görev Çalıştırıcısı Gezginini kullanabilirsiniz.

- [NPM görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) - *package.jsüzerinde* tanımlanan NPM betikleri için destek ekler. Yarn 'yi destekler.
- [WebPack görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) -WebPack için destek ekler.