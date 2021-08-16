---
title: Kod Ekleme hata ayıklaması | Microsoft Docs
description: 'Ekli kodu görüntülemek Visual Studio iki yol öğrenin: 1) Disassembly penceresinde; 2) hem ekleme hem de özgün kod olan bir kaynak dosyada.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f2bbeaaf88c482b89fc9832d5b80a4df2a6425db061159fadda446a83fcd46ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362230"
---
# <a name="how-to-debug-injected-code"></a>Nasıl Yapılır: Püskürtülen Kodda Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı Ayarlar'yi seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

Öznitelikleri kullanmak C++ programlamayı büyük ölçüde basitleştirebilir. Daha fazla bilgi için bkz. [Kavramlar.](/cpp/windows/attributed-programming-concepts) Bazı öznitelikler doğrudan derleyici tarafından yorumlanır. Diğer öznitelikler, derleyicinin derlediği program kaynağına kodlar da içerir. Bu kod, yazmanız gereken kod miktarını azaltarak programlamayı kolaylaştırır. Ancak, bazı durumlarda bir hata, uygulamanın eklenirken başarısız olmasına neden olabilir. Bu durumda, büyük olasılıkla kodun içine bakmak istersiniz. Visual Studio kodu görmenin iki yolu vardır:

- Ekleme kodunu, **Disassembly penceresinde görüntüebilirsiniz.**

- [/Fx kullanarak,](/cpp/build/reference/fx-merge-injected-code)özgün ve içine kod içeren birleştirilmiş bir kaynak dosyası oluşturabilirsiniz.

**Disassembly penceresi,** kaynak koda karşılık gelen derleme dili yönergelerini ve öznitelikler tarafından ekleme kodunu gösterir. Ayrıca, **Disassembly** penceresi kaynak kodu ek açıklamasını gösterebilir.

## <a name="to-turn-on-source-annotation"></a>Kaynak Ek Açıklamasını açmak için

- Ayır penceresine **sağ tıklayın ve** kısayol **menüsünden Kaynak Kodunu Göster'i** seçin.

     Bir özniteliğin kaynak penceresindeki konumunu biliyorsanız, eklenilen kodu **Disassembly** penceresinde bulmak için kısayol menüsünü kullanabilirsiniz.

## <a name="to-view-injected-code"></a>Yeni kod görüntülemek için

1. Hata ayıklayıcısı kesme modunda olması gerekir.

2. Kaynak kod penceresinde imleci, eklemek istediğiniz kodu özniteliğin önüne yerleştirebilirsiniz.

3. Sağ tıklayın ve kısayol **menüsünden Deassembly'ye** Git'i seçin.

     Öznitelik konumu geçerli yürütme noktasına yakınsa Hata  Ayıklama menüsünden Ayır penceresini **seçebilirsiniz.**

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Geçerli yürütme noktasındaki ayrık kodu görüntülemek için

1. Hata ayıklayıcısı kesme modunda olması gerekir.

2. Hata **Ayıkla menüsünden** Hata **Ayıkla'Windows'ye** **tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)