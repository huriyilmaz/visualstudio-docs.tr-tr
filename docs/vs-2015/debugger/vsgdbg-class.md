---
title: VsgDbg sınıfı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145701"
---
# <a name="vsgdbg-class"></a>VsgDbg Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik tanılama 'nın uygulama içi bileşeninin programlı denetimi için bir arabirim temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Üyeler  
 `VsgDbg`Sınıfı aşağıdaki üyeleri destekler.  
  
### <a name="public-constructors"></a>Ortak Oluşturucular  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Oluşturucu)](../debugger/vsgdbg-vsgdbg-constructor.md)|Sınıfının bir örneğini oluşturur `VsgDbg` ve isteğe bağlı olarak grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerini etkin bir şekilde yakalayıp kaydetmek üzere hazırlar.|  
|[VsgDbg::~VsgDbg (Yok Edici)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Sınıfının bir örneğini yok eder `VsgDbg` .|  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Grafik tanılama HUD (baş ekran) için özel bir ileti ekler.|  
|[BeginCapture](../debugger/begincapture.md)|İle biten bir yakalama aralığı başlatır `EndCapture` .|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Geçerli çerçevenin kalan kısmını grafik günlük dosyasına yakalar.|  
|[Kopyalama (Programlı Yakalama)](../debugger/copy-programmatic-capture.md)|Etkin grafik günlüğü (. vsglog) dosyasının içeriğini yeni bir dosyaya kopyalar.|  
|[EndCapture](../debugger/endcapture.md)|İle başlatılan bir yakalama aralığını sonlandırır `BeginCapture` .|  
|[Dengeleyici](../debugger/init.md)|Grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek üzere hazırlar.|  
|[ToggleHUD](../debugger/togglehud.md)|Grafik tanılama HUD kaplamasına açık veya kapalı olarak geçiş yapar.|  
|[UnInit](../debugger/uninit.md)|Grafik günlük dosyasını sonlandırır, kapatır ve uygulama grafik bilgilerini etkin bir şekilde kaydederken kullanılan kaynakları serbest bırakır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `VsgDbg`Sınıfı, grafik Tanılama özelliklerini programlama yoluyla denetlemek için kullanabileceğiniz bir arabirimi temsil eder. Grafik bilgilerini etkin bir şekilde yakalamaktan ve kaydetmeseniz bile bazı özellikleri kullanabilirsiniz; Bu, `AddMessage` üye işlev ve `ToggleHUD` üye işlevini içerir. Diğer üye işlevleri grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerinin etkin bir şekilde yakalanması veya durdurulması için hazırlayın ya da uygulama etkin bir şekilde yakalayıp grafik bilgilerini bir grafik günlüğü dosyasına kaydederken çağrılmalıdır.
