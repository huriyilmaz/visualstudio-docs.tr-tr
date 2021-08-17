---
title: System &apos; |'da Çekirdek Hata Ayıklayıcısı Etkinleştirildiğinden Hata Ayıklama | Microsoft Docs
description: Bu ileti, hata ayıklama modunda başlatan Windows 7 veya Windows Vista sisteminde yönetilen kodda hata ayıklamaya çalıştığınızda ve uygulama CLR CLR 2.0, 3.0 veya 3.5 sürümünü kullandığında oluşur.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8a09e47641ac8b94a3c7a60b39c4260bdd6ea5af
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036034"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Hata: Sistemde&#39;Hata Ayıklayıcısı Etkinleştirildiğinden Hata Ayıklama Mümkün Değil
Yönetilen kodda hata ayıklarken aşağıdaki hata iletisini alabilirsiniz:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Yönetilen kodda hata ayıklamaya çalışsanız bu ileti oluşur:

- hata [!INCLUDE[win7](../debugger/includes/win7_md.md)] ayıklama [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] modunda başlatan bir veya sisteminde.

- uygulama CLR CLR 2.0, 3.0 veya 3.5 sürümünü kullanır.

## <a name="solution"></a>Çözüm

#### <a name="to-fix-this-problem"></a>Bu sorunu düzeltmek için

- ClR sürüm 4.0 veya 4.5'i kullanmak için uygulamanızı yükseltin

   —veya—

- içinde çekirdek hata ayıklamayı ve hata ayıklamayı devre dışı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bırakma.

   —veya—

- yerine Çekirdek Hata Ayıklayıcı'sını kullanarak hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklar.

   —veya—

- Çekirdek Hata Ayıklayıcısı'da kullanıcı modu özel durumlarını devre dışı bırak.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Geçerli oturumda çekirdek hata ayıklamasını devre dışı bırakmak için

- Komut istemine şunları yazın:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Tüm oturumlarda çekirdek hata ayıklamasını devre dışı bırakmak için (Windows Vista ve Windows 7)

1. Komut istemine şunları yazın:

    ```cmd
    bcdedit /debug off
    ```

2. Bilgisayarı yeniden başlatın.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Tüm oturumlar (diğer işletim sistemleri) için çekirdek hata Windows devre dışı bırakmak için

1. Sistem boot.ini (genellikle C: ) konumlarını \\ bulun. boot.ini dosyası gizli ve salt okunur olabilir. Bu nedenle, bunu görmek için aşağıdaki komutu kullanabilirsiniz:

    ```cmd
    dir /ASH
    ```

2. Aşağıdaki boot.ini kullanarak Not Defteri ve aşağıdaki seçenekleri kaldırın:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Bilgisayarı yeniden başlatın.

#### <a name="to-debug-with-the-kernel-debugger"></a>Çekirdek Hata Ayıklayıcısı ile hata ayıklamak için

1. Çekirdek Hata Ayıklayıcısı'nın bağlı olduğu bir iletiyle hata ayıklamaya devam etmek isteyip istemediklerini sorarsınız. Devam etmek için düğmeye tıklayın.

2. Bu durumda hata `User break exception(Int 3).` ayıklamaya devam etmek için aşağıdaki Çekirdek Hata Ayıklayıcısı komutunu yazın:

     `gn`

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
