---
title: Node.js REPL kullanma
description: Visual Studio çalışma zamanıyla etkileşim kurmak için Node.js sağlar
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625785"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Node.js etkileşimli penceresiyle çalışma

Node.js araçları Visual Studio çalışma zamanı için etkileşimli bir pencere Node.js içerir. Bu pencere, JavaScript kodu girmenize ve sonuçları hemen görmenize ve geçerli projeyle etkileşim kurmak için npm komutlarını yürütmenize olanak sağlar. Etkileşimli pencere rePL **(R** ead/**E** değerli/**P** rint **Loop) olarak da** bilinir.

## <a name="open-the-interactive-window"></a>Etkileşimli pencereyi açma

Etkileşimli pencereyi açmak için, Node.js proje düğümüne sağ tık Çözüm Gezgini Etkileşimli **Pencere'Node.js aç'ı seçerek açabilirsiniz.**

![Node.js bağlam menüsünde etkileşimli pencereyi açma](../javascript/media/interactivewindow-open-from-project.png)

Etkileşimli pencereyi açmak için varsayılan kısa kesme Node.js **[CTRL] + K, N tuşlarıdır.** Ya da Etkileşimli Pencere'de Görüntüle'Windows   >  **Node.js**  >  **araç çubuğundan pencereyi açabilirsiniz.**

## <a name="use-the-repl"></a>REPL kullanma

Açıldıktan sonra komutları girebilirsiniz.

![Node.js etkileşimli pencere](../javascript/media/interactivewindow.png)

Etkileşimli pencerede, bunları bildiren herhangi bir JavaScript işlevinden ayırt etmek için nokta ön eki ile baş eden birkaç yerleşik komut vardır. Aşağıdaki komutlar de destekler:

**.cls, .clear** Geçmiş ve yürütme bağlamını olduğu gibi bırakarak düzenleyici penceresinin içeriğini temizler.

**.help** Belirtilen komutta veya hiçbiri belirtilmezse kullanılabilir tüm komutlarda ve anahtar bağlamalarında yardım görüntüler.

**.info** Geçerli kullanılan dosyanın yürütülebilir dosyası Node.js gösterir.

**.npm** Bir npm komutu çalıştırır. Çözüm birden fazla proje içeriyorsa kullanarak hedef projeyi `.npm [projectname] <npm arguments>` belirtin.

**.reset** Yürütme ortamını başlangıç durumuna sıfırlar, geçmişi tutma.

**.save** Geçerli REPL oturumunu bir dosyaya kaydeder.