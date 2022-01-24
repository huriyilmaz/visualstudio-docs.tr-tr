---
title: npm kullanarak TypeScript kodunu derleme ve derleme
description: Node Paket Yöneticisi (npm) kullanarak Visual Studio projelerinize TypeScript desteği eklemeyi öğrenin.
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
ms.openlocfilehash: 7f1c0618967577dd8b4585b71c3c99c76324ebcf
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650274"
---
# <a name="compile-typescript-code-nodejs"></a>TypeScript kodunu derleme (Node.js)

Projenize TypeScript desteği eklemek için TypeScript SDK npm'yi kullanın. Bu TypeScript SDK, varsayılan olarak Visual Studio kullanılabilir.

Visual Studio 2019'da geliştirilen projeler için, farklı platformlar ve ortamlar arasında daha fazla taşınabilirlik için TypeScript npm paketini kullanın.

Daha ASP.NET Core projelerde bunun yerine NuGet [önerilir.](../javascript/compile-typescript-code-nuget.md)

## <a name="add-typescript-support-using-npm"></a>npm kullanarak TypeScript desteği ekleme

[TypeScript npm paketi,](https://www.npmjs.com/package/typescript) TypeScript desteği ekler. Projenize TypeScript 2.1 veya daha yeni bir sürümü için npm paketi yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.

1. [Uygulama geliştirme](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) iş yükünü ve Node.js çalışma zamanının yükleme Node.js izleyin.

   Basit bir Visual Studio için Projenizi, Boş Node.js Web Uygulaması şablonu gibi Node.js TypeScript Node.js şablonlarından birini kullanarak oluşturun. Yoksa, Node.js'Node.js bir JavaScript şablonu Visual Studio yönergeleri izleyin. Veya bir Klasör Aç [projesini kullanabilirsiniz.](../javascript/develop-javascript-code-without-solutions-projects.md)

1. Projeniz henüz dahil etmemişse [TypeScript npm paketini yükleyin.](https://www.npmjs.com/package/typescript)

   Bu Çözüm Gezgini (sağ bölme) proje kökünde *package.json'u* açın. Listelenen paketler, Çözüm Gezgini'daki npm düğümü altındaki paketlere karşılık Çözüm Gezgini. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

   Bir Node.js için, komut satırı veya IDE kullanarak TypeScript npm paketini yükleyebilirsiniz. IDE kullanarak yüklemek için, Çözüm Gezgini'de npm düğümüne sağ tıklayın, Yeni npm paketini yükle'yi **seçin,** **TypeScript'i** arayın ve paketi yükleyin.

   Paket yükleme ilerlemesini görmek için **Çıkış** penceresinde **npm** seçeneğini işaretleyin. Yüklü paket, **Çözüm Gezgini'daki npm** düğümü altında Çözüm Gezgini.

1. Projeniz henüz eklemezse proje kök dosyanıza *bir .tsconfig* dosyası ekleyin. Dosyayı eklemek için proje düğümüne sağ tıklayın ve Yeni Öğeye **Ekle'> seçin.** **TypeScript JSON Yapılandırma Dosyasını seçin ve** ekle'ye **tıklayın.**

   Visual Studio *tsconfig.json dosyasını* proje köküne ekler. TypeScript derleyicisi seçeneklerini [yapılandırmak için](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) bu dosyayı kullanabilirsiniz.

1. *tsconfig.json'ı* açın ve istediğiniz derleyici seçeneklerini ayarlamak için güncelleştirin.

   Basit bir *tsconfig.json dosyası örneği* aşağıdaki gibidir.

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
   - *include,* derleyiciye TypeScript (*.ts) dosyalarının nerede bulun olduğunu söyler.
   - *outDir* seçeneği, TypeScript derleyicisi tarafından transpile edilen düz JavaScript dosyalarının çıkış klasörünü belirtir.
   - *sourceMap* seçeneği, derleyicinin sourceMap dosyaları *oluşturıp oluşturmay olmadığını* gösterir.

   Önceki yapılandırma, TypeScript'i yapılandırmaya yalnızca temel bir giriş sağlar. Diğer seçenekler hakkında bilgi için bkz. [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Uygulama oluşturma

1. Projenize TypeScript (*.ts*) veya TypeScript JSX (*.tsx*) dosyalarını ekleyin ve ardından TypeScript kodunu ekleyin. TypeScript'in basit bir örneği aşağıdaki gibidir:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. *package.json içinde,* aşağıdaki betikleri kullanarak Visual Studio ve temizleme komutları için destek ekleyin.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Webpack gibi üçüncü taraf bir araç kullanarak derlemek için *package.json* dosyanıza bir komut satırı derleme betiği ebilirsiniz:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Webpack'i React ve webpack yapılandırma dosyasıyla kullanma örneği için bkz. Node.js ve [React.](../javascript/tutorial-nodejs-with-react-and-jsx.md)

   TypeScript ile Vue.js örneği için [bkz. Vue.js uygulama oluşturma.](create-application-with-vuejs.md)

1. Başlangıç sayfası, Node.js çalışma zamanı, uygulama bağlantı noktası veya çalışma zamanı bağımsız değişkenleri gibi seçenekleri yapılandırmanız gerekirse, Çözüm Gezgini'de proje düğümüne sağ tıklayın ve Özellikler'i **seçin.**

   >[!NOTE]
   > Üçüncü taraf araçları yapılandırıldığında Node.js projeleri, Araçlar Seçenekler Projeleri ve çözümleri Web uygulaması Dış Web Araçları altında  >    >    >  **yapılandırılan Paket Yönetimi**  >  **kullanmaz.** Bu ayarlar diğer proje türleri için kullanılır.

1. Build **> Build Solution (Derleme Çözümü) seçin.**

   Uygulama, çalıştırılırken otomatik olarak oluşturulur. Ancak, derleme işlemi sırasında aşağıdakiler oluşabilir:

   Kaynak eşlemeleri oluşturduysanız *outDir* seçeneğinde belirtilen klasörü açın ve oluşturulan \*.js \* js.map dosyalarıyla birlikte bulursanız.

   Hata ayıklaması için kaynak eşleme [dosyaları gereklidir.](../javascript/debug-nodejs.md)

### <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı derledikten sonra çalıştırma yönergeleri için bkz. [İlk uygulama Node.js oluşturma.](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-app)

## <a name="automate-build-tasks"></a>Derleme görevlerini otomatikleştirme

npm ve webpack gibi üçüncü taraf Visual Studio için görevleri otomatikleştirmeye yardımcı olmak üzere görev çalıştırıcı gezginini Visual Studio içinde kullanabilirsiniz.

- [NPM Görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) - package.json içinde tanımlanan npm *betikleri için destek ekler.* yarn'i destekler.
- [Webpack Görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) - Webpack için destek ekler.