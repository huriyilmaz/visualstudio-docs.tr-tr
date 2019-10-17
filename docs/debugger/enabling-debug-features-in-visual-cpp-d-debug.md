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
ms.openlocfilehash: 7f772b74a42b9704f1fd77c731022ddb44774c68
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430674"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>C++ Projelerde hata ayıklama özelliklerini etkinleştirme (/D_DEBUG)
@No__t-0 ' da, bir hata ayıklama gibi hata ayıklama özellikleri, programınızı bir **_Debug** , tanımlı simgesiyle derlerken etkinleştirilir. **_Debug** 'ı iki şekilde tanımlayabilirsiniz:

- Kaynak kodunuzda **#define _HATA ayıklama** belirtin veya

- **/D_DEBUG** derleyici seçeneğini belirtin. (Sihirbazları kullanarak projenizi Visual Studio 'da oluşturursanız, **/D_DEBUG** hata ayıklama yapılandırmasında otomatik olarak tanımlanır.)

  **_Hata ayıklama** tanımlandığında, derleyici **#ifdef _debug** ve `#endif` ile çevrelenen kodun bölümlerini derler.

  MFC programının hata ayıklama yapılandırması MFC kitaplığının hata ayıklama sürümüyle bağlantı etmelidir. MFC üst bilgi dosyaları, tanımladığınız simgelere göre ( **_Debug** ve **_UNICODE**gıbı) bağlantılı olarak MFC kitaplığının doğru sürümünü belirlenir. Ayrıntılar için bkz. [MFC kitaplık sürümleri](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Ayrıca Bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)