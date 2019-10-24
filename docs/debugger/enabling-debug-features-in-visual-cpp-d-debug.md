---
title: C++ Projelerde hata ayıklama özelliklerini etkinleştirme (-D_DEBUG) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 19d341cba47e0a3d2259cc57d239c63420095347
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737950"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>C++ Projelerde hata ayıklama özelliklerini etkinleştirme (/D_DEBUG)
@No__t_0, programınızı derleme **_Hata ayıklama** simgesiyle derlerken onay gibi hata ayıklama özellikleri etkinleştirilir. **_Debug** 'ı iki şekilde tanımlayabilirsiniz:

- Kaynak kodunuzda **#define _HATA ayıklama** belirtin veya

- **/D_DEBUG** derleyici seçeneğini belirtin. (Sihirbazları kullanarak projenizi Visual Studio 'da oluşturursanız, **/D_DEBUG** hata ayıklama yapılandırmasında otomatik olarak tanımlanır.)

  **_Hata ayıklama** tanımlandığında, derleyici **#ifdef _debug** ve `#endif` ile çevrelenen kod bölümlerini derler.

  MFC programının hata ayıklama yapılandırması MFC kitaplığının hata ayıklama sürümüyle bağlantı etmelidir. MFC üst bilgi dosyaları, tanımladığınız simgelere göre ( **_Debug** ve **_UNICODE**gıbı) bağlantılı olarak MFC kitaplığının doğru sürümünü belirlenir. Ayrıntılar için bkz. [MFC kitaplık sürümleri](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)