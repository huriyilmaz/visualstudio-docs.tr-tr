---
title: Node.js REPL kullanın
description: Visual Studio Node.js çalışma zamanı ile etkileşim kurma desteği sağlar
ms.date: 12/04/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8b2bbbdf478f27f936d4897f2ff773baa4cca1d6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285010"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Etkileşimli Node.js penceresiyle çalışma

Visual Studio için Node.js araçları, yüklü Node.js çalışma zamanına yönelik etkileşimli bir pencere içerir. Bu pencere, JavaScript kodu girmenize ve sonuçları hemen görmenize olanak tanır. Ayrıca, geçerli projeyle etkileşimde bulunmak için NPM komutlarını yürütün. Etkileşimli pencere aynı zamanda REPL (**R**EAD/**E**valuate/**P**rint **L**OOP) olarak da bilinir.

## <a name="open-the-interactive-window"></a>Etkileşimli pencereyi aç

Etkileşimli pencereyi, Çözüm Gezgini Node.js proje düğümüne sağ tıklayıp **etkileşimli pencere aç Node.js**' ı seçerek açabilirsiniz.

![Proje bağlam menüsünde etkileşimli pencere Node.js](../javascript/media/interactivewindow-open-from-project.png)

Node.js etkileşimli pencereyi açmak için varsayılan kısa kesme tuşları **[Ctrl] + K, N**. Ya da **View**  >  **Windows**  >  **Node.js etkileşimli penceresini**görüntüle ' yi seçerek pencereyi araç çubuğundan açabilirsiniz.

## <a name="use-the-repl"></a>REPL kullanın

Açıldıktan sonra komutlar girebilirsiniz.

![Etkileşimli pencere Node.js](../javascript/media/interactivewindow.png)

Etkileşimli pencerede, bildirdiğiniz herhangi bir JavaScript işlevinden ayırt etmek için bir nokta önekiyle başlayan birkaç yerleşik komut vardır. Aşağıdaki komutlar desteklenir:

**. CLS,. Clear** , Geçmiş ve yürütme bağlamından ayrılmadan düzenleyici penceresinin içeriğini temizler.

**. yardım** Belirtilen komutla ilgili yardım ya da hiçbir şey belirtilmemişse tüm kullanılabilir komutlarda ve anahtar bağlamalarında yardım görüntüler.

**. INFO** Geçerli kullanılan Node.js çalıştırılabilir dosyası hakkındaki bilgileri gösterir.

**. NPM** Bir NPM komutu çalıştırır. Çözüm birden fazla proje içeriyorsa, öğesini kullanarak hedef projeyi belirtin `.npm [projectname] <npm arguments>` .

**. Reset** Yürütme ortamını ilk durumuna sıfırlar, geçmişi devam edin.

**. Kaydet** Geçerli REPL oturumunu bir dosyaya kaydeder.