---
title: Düğüm.js REPL kullanın
description: Visual Studio, Node.js çalışma süresi ile etkileşim için destek sağlar
ms.date: 12/04/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: faed930c60869010f740cf0a1e118a40299ce782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62840684"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Node.js etkileşimli penceresi ile çalışın

Visual Studio için Node.js Tools yüklü Düğüm.js çalışma zamanı için etkileşimli bir pencere içerir. Bu pencere, JavaScript kodunu girmenizi ve sonuçları hemen görmenizi ve geçerli projeyle etkileşimde bulunduğunuz npm komutlarını yürütmenizi sağlar. Etkileşimli pencere repl olarak da bilinir **(R**ead/**E**valuate/**P**rint **L**oop).

## <a name="open-the-interactive-window"></a>Etkileşimli pencereyi açma

Solution Explorer'daki Düğüm.js proje düğümüne sağ tıklayarak ve **Open Node.js Interactive Window'u**seçerek etkileşimli pencereyi açabilirsiniz.

![Proje bağlammenüsünde Düğüm.js etkileşimli pencere](../javascript/media/interactivewindow-open-from-project.png)

Düğüm.js etkileşimli pencereyi açmak için varsayılan kısa yol tuşları **[CTRL] + K, N**. Veya**Windows** > Düğümlerini **Görüntüle'yi** > seçerek pencereyi araç çubuğundan**açabilirsiniz.**

## <a name="use-the-repl"></a>REPL'yi kullanma

Açıldıktan sonra komutları girebilirsiniz.

![Düğüm.js etkileşimli pencere](../javascript/media/interactivewindow.png)

Etkileşimli pencere, beyan ettiğiniz herhangi bir JavaScript işlevinden ayırt etmek için nokta önekiyle başlayan birkaç yerleşik komuta sahiptir. Aşağıdaki komutlar desteklenir:

**.cls, .açık** Düzenleyici penceresinin içeriğini temizler ve geçmiş ve yürütme bağlamını bozulmadan bırakır.

**.yardım** Belirtilen komutta veya varsa tüm kullanılabilir komutlarda ve anahtar bağlamalarında yardım görüntüler.

**.info** Çalıştırılabilen geçerli düğüm.js hakkındaki bilgileri gösterir.

**.npm** NPM komutu çalıştırın. Çözüm birden fazla proje içeriyorsa, hedef `.npm [projectname] <npm arguments>`projeyi kullanarak belirtin.

**.sıfırlama** Yürütme ortamını ilk duruma sıfırlar, geçmişi korur.

**.kaydet** Geçerli REPL oturumunu bir dosyaya kaydeder.