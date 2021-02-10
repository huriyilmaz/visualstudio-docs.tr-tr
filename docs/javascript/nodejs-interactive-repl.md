---
title: Node.js REPL kullanın
description: Visual Studio Node.js çalışma zamanı ile etkileşim kurma desteği sağlar
ms.date: 12/04/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9f13128bc552ffdb31b3f4a9315a3f9aa3543b0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962697"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Etkileşimli Node.js penceresiyle çalışma

Visual Studio için Node.js araçları, yüklü Node.js çalışma zamanına yönelik etkileşimli bir pencere içerir. Bu pencere, JavaScript kodu girmenize ve sonuçları hemen görmenize olanak tanır. Ayrıca, geçerli projeyle etkileşimde bulunmak için NPM komutlarını yürütün. Etkileşimli pencere aynı zamanda REPL (**R** EAD/**E** valuate/**P** rint **L** OOP) olarak da bilinir.

## <a name="open-the-interactive-window"></a>Etkileşimli pencereyi aç

Etkileşimli pencereyi, Çözüm Gezgini Node.js proje düğümüne sağ tıklayıp **etkileşimli pencere aç Node.js**' ı seçerek açabilirsiniz.

![Proje bağlam menüsünde etkileşimli pencere Node.js](../javascript/media/interactivewindow-open-from-project.png)

Node.js etkileşimli pencereyi açmak için varsayılan kısa kesme tuşları **[Ctrl] + K, N**. Ya da   >  **Windows**  >  **Node.js etkileşimli penceresini** görüntüle ' yi seçerek pencereyi araç çubuğundan açabilirsiniz.

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