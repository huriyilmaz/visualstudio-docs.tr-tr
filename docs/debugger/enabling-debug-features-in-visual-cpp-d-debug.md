---
title: C++ projelerinde hata ayıklama özelliklerini etkinleştirme (-D_DEBUG) | Microsoft Docs
description: Visual C++, _DEBUG tanımlayarak hata ayıklama özelliklerini etkinleştirirsiniz. Bunu nasıl yapacağınızı öğrenin ve bir MFC programını hata ayıklamak üzere bağlamayı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1a2ead92108d66b54342019fc19702e7a6e53575
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862939"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>C++ projelerinde hata ayıklama özelliklerini etkinleştirme (/D_DEBUG)
' De [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] , program, tanımlı **_DEBUG** simgesiyle derlerken onay gibi hata ayıklama özellikleri etkinleştirilir. **_DEBUG** iki şekilde tanımlayabilirsiniz:

- Kaynak kodunuzda **#define _debug** belirtin veya

- **/D_DEBUG** derleyici seçeneğini belirtin. (Sihirbazları kullanarak Visual Studio 'da projenizi oluşturursanız **/D_DEBUG** hata ayıklama yapılandırmasında otomatik olarak tanımlanır.)

  **_DEBUG** tanımlandığında derleyici, **#ifdef _debug** ve ile çevrelenen kod bölümlerini derler `#endif` .

  MFC programının hata ayıklama yapılandırması MFC kitaplığının hata ayıklama sürümüyle bağlantı etmelidir. MFC başlık dosyaları, **_DEBUG** ve **_UNICODE** gibi tanımladığınız SIMGELERE göre bağlantı için MFC kitaplığının doğru sürümünü belirlenir. Ayrıntılar için bkz. [MFC kitaplık sürümleri](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)