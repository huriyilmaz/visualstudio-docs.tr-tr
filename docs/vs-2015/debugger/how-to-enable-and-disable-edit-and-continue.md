---
title: "Nasıl yapılır: Düzenle ve devam et 'i etkinleştirme ve devre dışı bırakma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689257"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Nasıl Yapılır: Düzenle ve Devam Et'i Etkinleştirme veya Devre Dışı Bırakma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tasarım zamanında Seçenekler iletişim kutusunda Düzenle ve devam et **seçeneklerini** etkinleştirebilir veya devre dışı bırakabilirsiniz. Hata ayıklarken bu ayarı değiştiremezsiniz.  
  
 Düzenle ve devam et yalnızca hata ayıklama yapılarında geçerlidir. Yerel C++ için Düzenle ve devam et seçeneği,/ıNCREUPı seçeneğinin kullanılmasını gerektirir.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Düzenle ve devam et 'i etkinleştirmek/devre dışı bırakmak için  
  
1. Hata ayıklama seçenekleri sayfasını açın (**Araçlar/Seçenekler/hata ayıklama**).  
  
2. Kategoriyi **Düzenle ve devam et** kategorisine gidin.  
  
3. Etkinleştirmek için **Düzenle ve devam et 'ı etkinleştir** onay kutusunu işaretleyin. Devre dışı bırakmak için onay kutusunu temizleyin.  
  
   > [!NOTE]
   > IntelliTrace etkinleştirilmişse ve hem IntelliTrace olaylarını hem de çağrı bilgilerini toplayıp, Düzenle ve devam et devre dışı bırakıldı. Daha fazla bilgi için bkz. [IntelliTrace 'ı yapılandırma](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. **Tamam**’a tıklayın.  
  
   Bu seçenekler hakkında daha fazla bilgi için bkz. [Genel, hata ayıklama, Seçenekler Iletişim kutusu](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenle ve Devam Et](../debugger/edit-and-continue.md)
