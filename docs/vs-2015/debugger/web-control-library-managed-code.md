---
title: Web denetim kitaplığı (yönetilen kod) | Microsoft Docs
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
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031f894eb2e117a213f4f9fbbf08ac57a1512d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688172"
---
# <a name="web-control-library-managed-code"></a>Web Kontrol Kitaplığı (Yönetilen Kod)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web denetim kitaplığı proje şablonu bir DLL oluşturur. Sınıf kitaplığı bir DLL olduğundan, doğrudan çalıştıramazsınız. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Denetimi katıştıran bir sayfa oluşturmalısınız. Daha fazla bilgi için bkz. [Web denetim kitaplığı şablonu](https://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Web denetim kitaplığında hata ayıklamak için (Yöntem 1)  
  
1. Var olan bir Web denetim kitaplığı projesi açın veya yeni bir tane oluşturun.  
  
2. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Denetimi katıştıran bir sayfa oluşturun.  
  
3. Test bandı barındıran Web sitesinde [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] adlı bir alt dizin oluşturun `/Code` .  
  
4. Denetimin kaynak kodunu `/Code` alt dizine kopyalayın.  
  
5. Kaynak kodunu `/Code` alt dizinde açın ve kesme noktaları ayarlayın.  
  
6. Test bandı işaret eden bir URL ile tarayıcı penceresi açın. Denetimdeki bir kesme noktasına isabet edilir ve hata ayıklamayı başlatabilirsiniz.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Web denetim kitaplığında hata ayıklamak için (Yöntem 2)  
  
1. Aynı çözümde konak uygulama projesini ve Web denetimi projesini oluşturun.  
  
2. **Çözüm Gezgini**, konak uygulamasına sağ tıklayın ve **Başvuru Ekle**' yi seçin.  
  
3. Web denetimi projesine bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web uygulamaları](../debugger/debugging-preparation-aspnet-web-applications.md)
