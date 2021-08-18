---
title: Node.js REPL kullanın
description: Visual Studio, Node.js çalışma zamanına etkileşim kurma desteği sağlar
ms.date: 12/04/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8dc3cbe7fef2c5940a8e87c2f085e52cdd7b2659
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048147"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Etkileşimli Node.js penceresiyle çalışma

Visual Studio için Node.js araçları, yüklü Node.js çalışma zamanına yönelik etkileşimli bir pencere içerir. Bu pencere, JavaScript kodu girmenize ve sonuçları hemen görmenize olanak tanır. Ayrıca, geçerli projeyle etkileşimde bulunmak için NPM komutlarını yürütün. Etkileşimli pencere aynı zamanda REPL (**R** EAD/**E** valuate/**P** rint **L** OOP) olarak da bilinir.

## <a name="open-the-interactive-window"></a>Etkileşimli pencereyi aç

Etkileşimli pencereyi, Çözüm Gezgini Node.js proje düğümüne sağ tıklayıp **etkileşimli pencere aç Node.js**' ı seçerek açabilirsiniz.

![Proje bağlam menüsünde etkileşimli pencere Node.js](../javascript/media/interactivewindow-open-from-project.png)

Node.js etkileşimli pencereyi açmak için varsayılan kısa kesme tuşları **[Ctrl] + K, N**. veya, pencereyi araç çubuğundan açmak için   >  **Windows**  >  **Node.js etkileşimli pencere**' yi seçerek açabilirsiniz.

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