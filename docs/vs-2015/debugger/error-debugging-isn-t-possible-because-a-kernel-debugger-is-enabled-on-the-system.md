---
title: 'Hata: sistemde bir çekirdek hata ayıklayıcısı etkinleştirildiğinden, ISN&#39;t hata ayıklaması mümkün | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f963ad2fbdad9453f6c6b853bc720034f613c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197070"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Hata: sistemde bir çekirdek hata ayıklayıcısı etkinleştirildiğinden, ISN&#39;t hata ayıklaması mümkün
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen kodda hata ayıklarken, aşağıdaki hata iletisini alabilirsiniz:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Bu ileti, yönetilen kodda hata ayıklamaya çalıştığınızda oluşur:  
  
- [!INCLUDE[win7](../includes/win7-md.md)] [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] hata ayıklama modunda başlatılan bir veya sisteminde.  
  
- uygulama CLR 2,0, 3,0 veya 3,5 CLR sürümünü kullanır.  
  
## <a name="solution"></a>Çözüm  
  
#### <a name="to-fix-this-problem"></a>Bu sorunu gidermek için  
  
- Uygulamanızı CLR sürüm 4,0 veya 4,5 kullanmak üzere yükseltin  
  
     —veya—  
  
- İçinde çekirdek hata ayıklamayı ve hata ayıklamayı devre dışı bırakın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     —veya—  
  
- Yerine çekirdek hata ayıklayıcısını kullanarak hata ayıklayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     —veya—  
  
- Çekirdek hata ayıklayıcısında Kullanıcı modu özel durumlarını devre dışı bırakın.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Geçerli oturumda çekirdek hata ayıklamasını devre dışı bırakmak için  
  
- Komut istemine şunları yazın:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Tüm oturumlarda çekirdek hata ayıklamayı devre dışı bırakmak için (Windows Vista ve Windows 7)  
  
1. Komut istemine şunları yazın:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2. Bilgisayarı yeniden başlatın.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Tüm oturumlarda çekirdek hata ayıklamayı devre dışı bırakmak için (diğer Windows işletim sistemleri)  
  
1. Sistem sürücünüzde boot.ini bulun (genellikle C: \\ ). boot.ini dosyası gizli ve salt okunurdur. Bu nedenle, görüntülemek için aşağıdaki komutu kullanmanız gerekir:  
  
    ```  
    dir /ASH  
    ```  
  
2. Not defteri 'Ni kullanarak boot.ini açın ve aşağıdaki seçenekleri kaldırın:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3. Bilgisayarı yeniden başlatın.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Çekirdek hata ayıklayıcı ile hata ayıklamak için  
  
1. Çekirdek hata ayıklayıcı bağlanarsa, hata ayıklamaya devam etmek isteyip istemediğinizi soran bir ileti görürsünüz. Devam etmek için düğmeye tıklayın.  
  
2. `User break exception(Int 3).`Bu durum oluşursa, hata ayıklamaya devam etmek için aşağıdaki çekirdek hata ayıklayıcı komutunu yazın:  
  
     `gn`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
