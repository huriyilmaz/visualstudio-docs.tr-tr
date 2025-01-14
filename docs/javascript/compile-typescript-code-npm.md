---
title: NPM kullanarak TypeScript kodu derleme ve derleme
description: düğüm Paket Yöneticisi (npm) kullanarak Visual Studio projelerinize TypeScript desteğinin nasıl ekleneceğini öğrenin.
ms.date: 01/10/2022
ms.topic: conceptual
ms.custom: devdivchpfy22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 4fa9b3e991a618e2cad1f0d32a9ab3b0fd1a4060
ms.sourcegitcommit: 429b2378ee21b5f473b26f4b4ea0a70372a34ec2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "137733368"
---
# <a name="compile-typescript-code-nodejs"></a>TypeScript kodunu derle (Node.js)

TypeScript SDK veya NPM kullanarak projelerinize TypeScript desteği ekleyebilirsiniz. TypeScript SDK, Visual Studio yükleyicisinde varsayılan olarak kullanılabilir.

Visual Studio 2019 ' de geliştirilen projeler için, farklı platformlar ve ortamlarda daha fazla taşınabilirlik sağlamak üzere TypeScript npm paketini kullanmanızı öneririz.

ASP.NET Core projeleri için, bunun yerine [NuGet paketini](../javascript/compile-typescript-code-nuget.md) kullanmanız önerilir.

## <a name="add-typescript-support-using-npm"></a>NPM kullanarak TypeScript desteği ekleme

[TypeScript NPM paketi](https://www.npmjs.com/package/typescript) TypeScript desteği ekler. TypeScript 2,1 veya üzeri için NPM paketi projenize yüklendiğinde, TypeScript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.

1. Node.js geliştirme iş yükünü ve Node.js çalışma zamanını yüklemek için [yönergeleri izleyin](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) .

   basit bir Visual Studio tümleştirme için, boş Node.js Web uygulaması şablonu gibi Node.js TypeScript şablonlarından birini kullanarak projenizi oluşturun. aksi durumda, Visual Studio eklenen Node.js JavaScript şablonunu kullanın ve buradaki yönergeleri izleyin. Ya da açık bir [klasör](../javascript/develop-javascript-code-without-solutions-projects.md) projesi kullanın.

1. Projeniz zaten içermiyorsa, [TypeScript NPM paketini](https://www.npmjs.com/package/typescript)yükledikten sonra.

   Çözüm Gezgini (sağ bölme) menüsünde, proje kökünde *Package. JSON* öğesini açın. Listelenen paketler, Çözüm Gezgini NPM düğümü altındaki paketlere karşılık gelir. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](../javascript/npm-package-management.md).

   Node.js bir proje için, komut satırını veya IDE 'yi kullanarak TypeScript NPM paketini yükleyebilirsiniz. IDE kullanarak yüklemek için Çözüm Gezgini NPM düğümüne sağ tıklayın, **Yeni NPM paketi yüklensin**' i seçin, **TypeScript** için arama yapın ve paketi yüklemek için.

   Paket yükleme ilerlemesini görmek için **Çıkış** penceresindeki **NPM** seçeneğini işaretleyin. Yüklü paket, Çözüm Gezgini **NPM** düğümünün altında görüntülenir.

1. Projeniz zaten içermiyorsa, proje köküne bir *tsconfig. JSON* dosyası ekleyin. Dosyayı eklemek için, proje düğümüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TYPESCRIPT JSON yapılandırma dosyasını** seçin ve ardından **Ekle**' ye tıklayın.

   Visual Studio *tsconfig. json* dosyasını proje köküne ekler. TypeScript derleyicisi [seçeneklerini yapılandırmak](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) için bu dosyayı kullanabilirsiniz.

1. İstediğiniz derleyici seçeneklerini ayarlamak için *tsconfig. JSON* ve Update 'i açın.

   Basit *tsconfig. JSON* dosyasına bir örnek aşağıda verilmiştir.

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

   Önceki yapılandırma TypeScript 'i yapılandırmaya yönelik temel bir giriş sağlar. Diğer seçenekler hakkında daha fazla bilgi için bkz. [tsconfig. JSON](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Uygulama oluşturma

1. Projenize TypeScript (*. TS*) veya TypeScript JSX (*. TSX*) dosyaları ekleyin ve ardından TypeScript kodu ekleyin. TypeScript 'in basit bir örneği aşağıda verilmiştir:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. *package. json*' da aşağıdaki komut dosyalarını kullanarak Visual Studio derleme ve temizleme komutları için destek ekleyin.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   WebPack gibi bir üçüncü taraf araç kullanarak derlemek için *Package. JSON* dosyanıza bir komut satırı derleme betiği ekleyebilirsiniz:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   webpack 'i React ve bir webpack yapılandırma dosyası ile kullanmayla ilgili bir örnek için bkz. [Node.js ve React ile web uygulaması oluşturma](../javascript/tutorial-nodejs-with-react-and-jsx.md).

   TypeScript ile Vue.js kullanmayla ilgili bir örnek için bkz. [Vue.js uygulaması oluşturma](create-application-with-vuejs.md).

1. Başlangıç sayfası, Node.js çalışma zamanı, uygulama bağlantı noktası veya çalışma zamanı bağımsız değişkenlerinin yolu gibi seçenekleri yapılandırmanız gerekirse, Çözüm Gezgini proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.

   >[!NOTE]
   > Üçüncü taraf araçları yapılandırırken Node.js projeler, **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **Web paket yönetimi**  >  **dış Web araçları** altında yapılandırılan yolları kullanmaz. Bu ayarlar diğer proje türleri için kullanılır.

1. **Build > Build Solution** öğesini seçin.

   Uygulama, çalıştırdığınızda otomatik olarak oluşturulur. Bununla birlikte, oluşturma işlemi sırasında aşağıdakiler olabilir:

   Kaynak haritaları oluşturduysanız, *OutDir* seçeneğinde belirtilen klasörü açın ve oluşturulan \*.js dosya (lar) ı ile birlikte bulunan \* js. Map dosyalarını bulun.

   [Hata ayıklama](../javascript/debug-nodejs.md)için kaynak eşleme dosyaları gereklidir.

### <a name="run-the-application"></a>Uygulamayı çalıştırma

Derlemeden sonra uygulamayı çalıştırma yönergeleri için, bkz. [ilk Node.js uygulamanızı oluşturma](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-app).

## <a name="automate-build-tasks"></a>Derleme görevlerini otomatikleştirin

npm ve webpack gibi üçüncü taraf araçlara yönelik görevleri otomatikleştirmeye yardımcı olması için Visual Studio ' de görev çalıştırıcısı gezginini kullanabilirsiniz.

- [NPM görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) - *Package. JSON* içinde tanımlanan NPM betikleri için destek ekler. Yarn 'yi destekler.
- [WebPack görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) -WebPack için destek ekler.