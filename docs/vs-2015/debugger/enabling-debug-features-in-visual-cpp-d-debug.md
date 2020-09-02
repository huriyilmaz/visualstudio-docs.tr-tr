---
title: Visual C++ hata ayıklama özelliklerini etkinleştirme (-D_DEBUG) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cffa8592c2048c6c6b39eee5c4ca654c41448933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686700"
---
# <a name="enabling-debug-features-in-visual-c-d_debug"></a>Visual C++'de Hata Ayıklama Özelliklerini Etkinleştirme (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

' De [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , program, tanımlı **_DEBUG** simgesiyle derlerken onay gibi hata ayıklama özellikleri etkinleştirilir. **_DEBUG** iki şekilde tanımlayabilirsiniz:  
  
- Kaynak kodunuzda **#define _debug** belirtin veya  
  
- **/D_DEBUG** derleyici seçeneğini belirtin. (Sihirbazları kullanarak Visual Studio 'da projenizi oluşturursanız **/D_DEBUG** hata ayıklama yapılandırmasında otomatik olarak tanımlanır.)  
  
  **_DEBUG** tanımlandığında derleyici, **#ifdef _debug** ve ile çevrelenen kod bölümlerini derler `#endif` .  
  
  MFC programının hata ayıklama yapılandırması MFC kitaplığının hata ayıklama sürümüyle bağlantı etmelidir. MFC başlık dosyaları, **_DEBUG** ve **_UNICODE**gibi tanımladığınız SIMGELERE göre bağlantı için MFC kitaplığının doğru sürümünü belirlenir. Ayrıntılar için bkz. [MFC kitaplık sürümleri](https://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
