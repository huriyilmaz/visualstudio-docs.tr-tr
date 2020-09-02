---
title: 'Nasıl yapılır: eklenen kodda hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df35a25534961c6ab94891d2da6fe54f05c37a3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681084"
---
# <a name="how-to-debug-injected-code"></a>Nasıl Yapılır: Püskürtülen Kodda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Öznitelikleri kullanmak C++ programlamayı büyük ölçüde basitleştirebilir. Daha fazla bilgi için bkz. [Kavramlar](https://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Bazı öznitelikler doğrudan derleyici tarafından yorumlanır. Diğer öznitelikler, kodu program kaynağına ekler ve derleyicinin daha sonra derler. Bu eklenen kod, yazmanız gereken kod miktarını azaltarak programlamayı kolaylaştırır. Ancak bazen bir hata, eklenen kodu yürütürken uygulamanızın başarısız olmasına neden olabilir. Bu durumda muhtemelen eklenen koda bakmak isteyeceksiniz. Visual Studio, eklenen kodu görmeniz için iki yol sunar:  
  
- Eklenen kodu **ayrıştırma** penceresinde görebilirsiniz.  
  
- [/FX](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560)kullanarak, özgün ve eklenen kodu içeren bir birleştirilmiş kaynak dosya oluşturabilirsiniz.  
  
  **Ayrıştırılmış** pencere, kaynak koda ve öznitelikler tarafından eklenen koda karşılık gelen derleme dili talimatlarını gösterir. Ayrıca, **ayrıştırılmış** pencere, kaynak kodu ek açıklamasını gösterebilir.  
  
### <a name="to-turn-on-source-annotation"></a>Kaynak ek açıklamasını açmak için  
  
- **Ayrıştırma** penceresini sağ tıklatın ve kısayol menüsünden **kaynak kodunu göster** ' i seçin.  
  
     Bir özniteliğin konumunu kaynak pencerede biliyorsanız, eklenen kodu **ayrıştırma** penceresinde bulmak için kısayol menüsünü kullanabilirsiniz.  
  
### <a name="to-view-injected-code"></a>Eklenen kodu görüntülemek için  
  
1. Hata ayıklayıcı kesme modunda olmalıdır.  
  
2. Bir kaynak kodu penceresinde, eklenen kodu görüntülemek istediğiniz özniteliğin önüne imleci yerleştirin.  
  
3. Sağ tıklayın ve kısayol menüsünde **ayrıştırılmış koda git** ' i seçin.  
  
     Öznitelik konumu geçerli yürütme noktasının yakınında ise **hata ayıklama** menüsünden **ayrıştırma** penceresini seçebilirsiniz.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Geçerli yürütme noktasındaki ayrıştırılmış kodu görüntülemek için  
  
1. Hata ayıklayıcı kesme modunda olmalıdır.  
  
2. **Hata Ayıkla** menüsünde **Windows**' u seçin ve **ayrıştırılmış derleme**' ye tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
