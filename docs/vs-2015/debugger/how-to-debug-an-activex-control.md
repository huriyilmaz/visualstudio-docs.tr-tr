---
title: 'Nasıl yapılır: ActiveX denetiminde hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704460"
---
# <a name="how-to-debug-an-activex-control"></a>Nasıl Yapılır: ActiveX Denetiminde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 ActiveX denetimi hata ayıklaması yapmak için denetimin içinde çalışacağı bir kapsayıcı (yürütülebilir) belirtmeniz gerekir.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Hata ayıklama oturumu için bir kapsayıcı belirtmek için  
  
1. Çözüm Gezgini, projeyi seçin.  
  
2. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.  
  
3. **Proje özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörünü açın ve **hata ayıklama**öğesini seçin.  
  
4. **Hata ayıklama** kategorisi altında, **komut** özelliğini bulun.  
  
5. Kapsayıcının yol adını belirtin. Örneğin, C:\Program Files\ınternet Explorer\IEXPLORE.EXE.  
  
6. Kapsayıcı olarak Internet Explorer 'ı belirtirseniz ve etkin masaüstü kullanıyorsanız, `/new` **komut bağımsız değişkenleri** kutusuna yazın.  
  
7. **Tamam**’a tıklayın.  
  
     **Proje özellik sayfaları** iletişim kutusunda bir kapsayıcı belirtmezseniz, hata ayıklamaya başladığınızda kapsayıcıyı belirtebilirsiniz. Hata ayıklamayı başlatmak için bir yürütme komutu seçtiğinizde, [hata ayıklama oturumu Için yürütülebilir Iletişim kutusu](../debugger/executable-for-debugging-session-dialog-box.md) görüntülenir. İletişim kutusunda kapsayıcının yol adını belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ActiveX denetimleri](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Test kapsayıcısı ile özellikleri ve olayları test etme](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [COM ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md)   
 [Visual Studio'da Hata Ayıklama](../debugger/debugging-in-visual-studio.md)
