---
title: Eklenen kodda hata ayıkla | Microsoft Docs
description: "Birleştirme penceresinde Visual Studio 'Nun eklenen kodu görüntülemek için sağladığı iki yolu öğrenin: 1). 2) eklenen ve özgün koda sahip bir kaynak dosyada."
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
ms.workload:
- multiple
ms.openlocfilehash: c776303d22ad7f0b48a5f7c5361750f70c1ce6b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913238"
---
# <a name="how-to-debug-injected-code"></a>Nasıl Yapılır: Püskürtülen Kodda Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

Öznitelikleri kullanmak C++ programlamayı büyük ölçüde basitleştirebilir. Daha fazla bilgi için bkz. [Kavramlar](/cpp/windows/attributed-programming-concepts). Bazı öznitelikler doğrudan derleyici tarafından yorumlanır. Diğer öznitelikler, kodu program kaynağına ekler ve derleyicinin daha sonra derler. Bu eklenen kod, yazmanız gereken kod miktarını azaltarak programlamayı kolaylaştırır. Ancak bazen bir hata, eklenen kodu yürütürken uygulamanızın başarısız olmasına neden olabilir. Bu durumda muhtemelen eklenen koda bakmak isteyeceksiniz. Visual Studio, eklenen kodu görmeniz için iki yol sunar:

- Eklenen kodu **ayrıştırma** penceresinde görebilirsiniz.

- [/FX](/cpp/build/reference/fx-merge-injected-code)kullanarak, özgün ve eklenen kodu içeren bir birleştirilmiş kaynak dosya oluşturabilirsiniz.

**Ayrıştırılmış** pencere, kaynak koda ve öznitelikler tarafından eklenen koda karşılık gelen derleme dili talimatlarını gösterir. Ayrıca, **ayrıştırılmış** pencere, kaynak kodu ek açıklamasını gösterebilir.

## <a name="to-turn-on-source-annotation"></a>Kaynak ek açıklamasını açmak için

- **Ayrıştırma** penceresini sağ tıklatın ve kısayol menüsünden **kaynak kodunu göster** ' i seçin.

     Bir özniteliğin konumunu kaynak pencerede biliyorsanız, eklenen kodu **ayrıştırma** penceresinde bulmak için kısayol menüsünü kullanabilirsiniz.

## <a name="to-view-injected-code"></a>Eklenen kodu görüntülemek için

1. Hata ayıklayıcı kesme modunda olmalıdır.

2. Bir kaynak kodu penceresinde, eklenen kodu görüntülemek istediğiniz özniteliğin önüne imleci yerleştirin.

3. Sağ tıklayın ve kısayol menüsünde **ayrıştırılmış koda git** ' i seçin.

     Öznitelik konumu geçerli yürütme noktasının yakınında ise **hata ayıklama** menüsünden **ayrıştırma** penceresini seçebilirsiniz.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Geçerli yürütme noktasındaki ayrıştırılmış kodu görüntülemek için

1. Hata ayıklayıcı kesme modunda olmalıdır.

2. **Hata Ayıkla** menüsünde **Windows**' u seçin ve **ayrıştırılmış derleme**' ye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)