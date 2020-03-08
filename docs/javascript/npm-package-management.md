---
title: npm paketlerini yönetme
description: Visual Studio Node.js paket yöneticisini (npm) kullanarak paketleri yönetmenize yardımcı olur.
ms.custom: seodec18
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: de92c3f1f0d0e29d1ba2dfaf5d536a42e636be2c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409452"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio'da npm paketlerini yönetme

npm yükleme ve Node.js uygulamalarınızda kullanım için paketleri yönetme sağlar. NPM 'yi tanımıyorsanız ve daha fazla bilgi edinmek istiyorsanız [NPM belgelerine](https://docs.npmjs.com/)gidin.

Visual Studio, npm ve sorunu npm komutları ile kullanıcı Arabirimi aracılığıyla ya da doğrudan etkileşim kurmak kolaylaştırır. Aşağıdaki yöntemleri kullanabilirsiniz:
* [Paketleri Çözüm Gezgini 'dan yükler](#npmInstallWindow)
* [Yüklü paketleri Çözüm Gezgini yönetin](#solutionExplorer)
* [Node. js etkileşimli penceresindeki `.npm` komutunu kullanın](#interactive)

Bu özellikler birlikte çalışarak proje sistemiyle ve projedeki *Package. JSON* dosyasıyla eşitlenir.

> [!Important]
> NPM, proje kökünde *node_modules* klasörü ve *Package. JSON* bekliyor. Uygulamanızın klasör yapısı farklıysa, Visual Studio 'Yu kullanarak NPM paketlerini yönetmek istiyorsanız klasör yapınızı güncelleştirmeniz gerekir.

> [!NOTE]
> Mevcut NPM projeleri için, **mevcut Node. js kod** çözümü şablonunu kullanın.

## <a name="npmInstallWindow"></a>Paketleri Çözüm Gezgini 'dan yükler

Npm paket yükleme penceresi npm paketlerini yüklemek için en kolay yoludur. Bu pencereye erişmek için, projedeki **NPM** düğümüne sağ tıklayın ve **Yeni NPM paketleri yüklensin**' i seçin.

![Çözüm Gezgini'nden yeni npm paketini yükleme](../javascript/media/solution-explorer-install-package.png)

Bu pencerede bir paket için arama seçenekleri belirtin ve yükleyin.

![Arama npm paketi](../javascript/media/search-package.png)

* **Bağımlılık türü** - **Standart**, **geliştirme**ve **isteğe bağlı** paketler arasında tercih edin. Standart belirtir paketi bir çalışma zamanı bağımlılık olduğunu geliştirme paket yalnızca olduğunu belirten ancak geliştirme sırasında gerekli.
* **Package. JSON öğesine Ekle** -Bu seçenek kullanım dışıdır
* **Seçili sürüm** -yüklemek istediğiniz paketin sürümünü seçin.
* **Diğer NPM bağımsız değişkenleri** -diğer standart NPM bağımsız değişkenlerini belirtin. Örneğin, sürümler listesinde kullanılamayan belirli bir sürümü yüklemek için `@~0.8` gibi bir sürüm değeri girebilirsiniz.

Çıktı penceresinde npm sekmesinde Yükleme ilerlemesini görebilirsiniz. Bu işlem biraz zaman alabilir.

> [!TIP]
> Arama sorgusunu ilgilendiğiniz kapsama göre ön bekleyen paketler için arama yapabilirsiniz, örneğin, Mocha için TypeScript tanım dosyalarını aramak üzere `@types/mocha` yazın. Ayrıca, TypeScript için tür tanımlarını yüklerken, NPM bağımsız değişkeni alanına `@ts2.6` ekleyerek tardığınızda TypeScript sürümünü belirtebilirsiniz.

## <a name="solutionExplorer"></a>Çözüm Gezgini yüklü paketleri yönetme

npm paketlerini, Çözüm Gezgini'nde gösterilir. **NPM** düğümündeki girişler *Package. JSON* dosyasındaki bağımlılıkları taklit ediyor.

![Arama npm paketi](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paket durumu
* ![Yüklü paketleri](../javascript/media/installed-npm.png) -Yüklü ve listelenen package.json
* ![yabancı paket](../javascript/media/extraneous-npm.png)-yüklendi, ancak Package. JSON içinde açıkça listelenmemiş.
* ![Paket eksik](../javascript/media/missing-npm.png) -Not yüklendi, ancak listelenen Package.json'da

Aşağıdaki eylemlerden birini gerçekleştirmek için bir paket düğümüne veya **NPM** düğümüne sağ tıklayın:
* *Package. JSON* içinde listelenen **eksik paketleri yükler**
* **Paketleri** en son sürüme Güncelleştir
* **Bir paketi kaldırın** ve *Package. JSON* öğesinden kaldırın

## <a name="interactive"></a>Node. js etkileşimli penceresinde. NPM komutunu kullanın

NPM komutlarını yürütmek için Node. js etkileşimli penceresindeki `.npm` komutunu da kullanabilirsiniz. Pencereyi açmak için Çözüm Gezgini içinde projeye sağ tıklayın ve **Node. js etkileşimli penceresini aç**' ı seçin.

Pencerede, paketi yüklemek için aşağıdaki gibi komutları kullanabilirsiniz:

`.npm install azure@4.2.3`

 > [!Tip]
 > Varsayılan olarak, projenizin giriş dizininde npm yürütülür. Çözümünüz içinde birden çok proje varsa, köşeli ayraç içinde adı veya projesinin yolunu belirtin.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Projeniz bir Package. JSON dosyası içermiyorsa, varsayılan girdilerle yeni bir Package. JSON dosyası oluşturmak için `.npm init -y` kullanın.
