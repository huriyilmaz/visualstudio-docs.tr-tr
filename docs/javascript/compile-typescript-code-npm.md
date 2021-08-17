---
title: npm kullanarak TypeScript kodunu derleme ve derleme
description: Node Paket Yöneticisi (npm) kullanarak Visual Studio projelerinize Typescript desteği eklemeyi öğrenin.
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
ms.openlocfilehash: 98e87e402613e73dd9a5ab8a08f3c2bdae1ab1d2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055763"
---
# <a name="compile-typescript-code-nodejs"></a>TypeScript kodunu derleme (Node.js)

TypeScript SDK yükleyicisinde varsayılan olarak kullanılabilir olan Visual Studio npm kullanarak projelerinize TypeScript desteği ekleme. Visual Studio 2019'da geliştirilen projeler için, farklı platformlar ve ortamlar arasında daha fazla taşınabilirlik için TypeScript npm paketini kullanın.

Daha ASP.NET Core projelerde bunun yerine NuGet [önerilir.](../javascript/compile-typescript-code-nuget.md)

## <a name="add-typescript-support-using-npm"></a>npm kullanarak TypeScript desteği ekleme

[TypeScript npm paketi,](https://www.npmjs.com/package/typescript) TypeScript desteği ekler. Projenize TypeScript 2.1 veya daha yeni bir sürümü için npm paketi yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.

1. [Uygulama geliştirme](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) iş yükünü ve Node.js çalışma zamanının yükleme Node.js izleyin.

   Visual Studio ile en basit tümleştirme için, Boş Node.js Web Uygulaması şablonu gibi Node.js TypeScript şablonlarından birini kullanarak projenizi oluşturun. Aksi takdirde, Node.js bir JavaScript şablonu Visual Studio buradaki yönergeleri izleyin veya bir Klasör Aç [projesini](../javascript/develop-javascript-code-without-solutions-projects.md) kullanın.

1. Projeniz henüz dahil etmemişse [TypeScript npm paketini yükleyin.](https://www.npmjs.com/package/typescript)

   Bu Çözüm Gezgini (sağ bölme) proje *kökündepackage.jsaçık* olan bölmeyi açın. Listelenen paketler, Çözüm Gezgini'daki npm düğümü altındaki paketlere karşılık Çözüm Gezgini. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

   Bir Node.js için, komut satırı veya IDE kullanarak TypeScript npm paketini yükleyebilirsiniz. IDE kullanarak yüklemek için, Çözüm Gezgini'de npm düğümüne sağ tıklayın, Yeni npm paketini yükle'yi **seçin,** **TypeScript** araması yazın ve paketi yükleyin.

   Paket yükleme ilerlemesini görmek için **Çıkış** penceresinde **npm** seçeneğini işaretleyin. Yüklü paket, **Çözüm Gezgini'daki npm** düğümü altında Çözüm Gezgini.

1. Projeniz henüz eklemezse proje kök dosyanıza *bir .tsconfig* dosyası ekleyin. Dosyayı eklemek için proje düğümüne sağ tıklayın ve Yeni Öğeye **Ekle'> seçin.** **TypeScript JSON Yapılandırma Dosyasını seçin ve** ekle'ye **tıklayın.**

   Visual Studio, *tsconfig.jsproje* köküne ekler. TypeScript derleyicisi seçeneklerini [yapılandırmak için](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) bu dosyayı kullanabilirsiniz.

1. Açık *tsconfig.jsve* güncelleştirmeyi açıp istediğiniz derleyici seçeneklerini ayarlayın.

   Aşağıda, dosyada basit birtsconfig.js *örneği ve* ardından ve bir örnek ve açıklama ve açıklama yer aleladedir.

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

   Önceki yapılandırma, TypeScript'i yapılandırmaya yalnızca temel bir giriş sağlar. Diğer seçenekler hakkında bilgi için [bkz.tsconfig.js.](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

## <a name="build-the-application"></a>Uygulama oluşturma

1. Projenize TypeScript (*.ts*) veya TypeScript JSX (*.tsx*) dosyalarını ekleyin ve ardından TypeScript kodunu ekleyin. Basit bir TypeScript örneği için aşağıdakini kullanın:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. üzerinde *package.js,* aşağıdaki betikleri kullanarak Visual Studio ve temizleme komutları için destek ekleyin.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Webpack gibi bir üçüncü taraf aracı kullanarak derlemeniz gerekirse, dosya üzerinde dosyanıza bir komut satırı *derlemepackage.jsabilirsiniz:*

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Webpack'i React ve webpack yapılandırma dosyasıyla kullanma örneği için bkz. Node.js ve [React.](../javascript/tutorial-nodejs-with-react-and-jsx.md)

   TypeScript ile Vue.js örneği için [bkz. Vue.js uygulaması oluşturma.](/javascript/create-application-with-vuejs)

1. Başlangıç sayfası, Node.js çalışma zamanı, uygulama bağlantı noktası veya çalışma zamanı bağımsız değişkenleri gibi seçenekleri yapılandırmanız gerekirse, Çözüm Gezgini proje düğümüne sağ tıklayın ve Özellikler'i **seçin.**

   >[!NOTE]
   > Üçüncü taraf araçları yapılandırıldığında, Node.js projeleri, Araçlar Seçenekler Projeleri ve çözümleri Web Uygulaması Dış Web Araçları altında  >    >    >  **Paket Yönetimi**  >  **yolları kullanmaz.** Bu ayarlar diğer proje türleri için kullanılır.

1. Derleme **ve Derleme >'ı seçin.**

   Uygulamayı çalıştırarak otomatik olarak derlemeye devam ediyor olsa da, derleme işlemi sırasında olan bir şeye göz atacağız:

   Kaynak eşlemeleri oluşturduysanız *outDir* seçeneğinde belirtilen klasörü açın ve oluşturulan \*.js \* js.map dosyalarıyla birlikte bulursanız.

   Hata ayıklaması için kaynak eşleme [dosyaları gereklidir.](../javascript/debug-nodejs.md)

### <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı derledikten sonra çalıştırma yönergeleri için bkz. [İlk uygulamanızı Node.js oluşturma.](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-app)

## <a name="automate-build-tasks"></a>Derleme görevlerini otomatikleştirme

npm ve webpack gibi üçüncü taraf Visual Studio otomatikleştirmeye yardımcı olmak için görev çalıştırıcısı Gezgini'ni kullanabilirsiniz.

- [NPM Görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) - 'de tanımlanan npm *betikleripackage.jsekler.* yarn'i destekler.
- [Webpack Görev Çalıştırıcısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) - Webpack için destek ekler.
