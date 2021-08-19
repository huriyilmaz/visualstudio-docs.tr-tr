---
title: UWP uygulamalarını dağıtma | Microsoft Docs
description: Visual Studio Evrensel Windows Platformu (UWP) uygulamalarını dağıtın. Dağıtım için yerel veya uzak bir hedef cihaz belirtin. Dağıtım seçeneklerini anlayın.
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 686448117cdb112c9136091a951853b275947ea6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080958"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Visual Studio’dan UWP uygulamaları dağıtma

Visual Studio dağıtım işlevselliği, bir hedef cihazda Visual Studio ile oluşturulan UWP uygulamalarını oluşturur ve kaydeder. Uygulamanın nasıl kaydedildiği, hedef cihazın yerel mi yoksa uzak mı olduğuna bağlıdır:

- hedef yerel Visual Studio makinediğinde, Visual Studio uygulamayı build klasöründen kaydeder.

- hedef uzak bir cihaz olduğunda, Visual Studio gerekli dosyaları uzak makineye kopyalar ve uygulamayı bu cihaza kaydeder.

**hata ayıklamayı başlat** seçeneğini (klavye: F5) veya **hata ayıklama olmadan başlat** seçeneğini (klavye: CTRL + f5) kullanarak Visual Studio uygulamanızda hata ayıklaması yaptığınızda dağıtım otomatik olarak gerçekleştirilir. Uygulamanızı el ile de dağıtabilirsiniz. Aşağıdaki senaryolarda el ile dağıtım yararlı olur:

- Yerel veya uzak bir makinede geçici test.

- Hata ayıklamak istediğiniz başka bir uygulamayı başlatacak bir uygulama dağıtma.

- Başka bir uygulama veya yöntem tarafından başlatıldığında Ayıklanacak bir uygulama dağıtma.

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> UWP uygulaması dağıtma
 Uygulamayı el ile dağıtmak basit bir işlemdir:

1. Uzak bir cihaza dağıtıyorsanız, uygulamanın başlangıç projesinin Özellik projesi sayfasında cihazın adını veya IP adresini belirtin. (Bunu yapmak için adımlar bu konuda daha sonra listelenmiştir.).

2. hata ayıklayıcı Visual Studio araç çubuğunda, **hata ayıklamayı başlat** düğmesinin yanındaki açılan listeden dağıtım hedefini seçin.

     ![Yerel makinede Çalıştır](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. **Yapı** menüsünde **Dağıt** ' ı seçin.

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Uzak cihaz belirtme

**Önkoşullar**

Windows 10 uzak bir cihazda [geliştirici modunu](/windows/uwp/get-started/enable-your-device-for-development)etkinleştirmeniz gerekir. oluşturucunun güncelleştirme veya sonrasını çalıştıran Windows 10 cihazlarda, uygulamanızı dağıtırken uzak araçlar otomatik olarak yüklenir. Daha fazla bilgi için bkz. [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Windows 10 'nin ön oluşturana ait güncelleştirme sürümlerinde, Visual Studio için Uzak Araçlar uzak cihaza yüklenmelidir ve uzaktan hata ayıklayıcı çalışıyor olmalıdır.

Dağıtım, uzak cihaza uygulama dosyalarını göndermek için uzaktan hata ayıklayıcı ağ kanalını kullanır.

#### <a name="to-specify-a-remote-device"></a>Uzak bir cihaz belirtmek için

1. Başlangıç projesinin hata ayıklama özelliği sayfasında, uzak dağıtım hedefinin adını veya IP adresini belirtin.

2. Hata ayıklama özelliği sayfasını açmak için Çözüm Gezgini ' de projeyi seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

3. Sonra özellik sayfaları penceresinde **hata ayıklama** düğümünü seçin.

4. **Hedef cihaz** Için **uzak makine**' yi seçin.

5. **Uzak makine** altında **bul**' a tıklayın.

6. Uzak cihazın adını veya IP adresini yazabilir veya **uzak bağlantı** iletişim kutusundan cihazı seçebilirsiniz.

    ![Uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **uzak bağlantı** iletişim kutusu, yerel ağ alt ağındaki cihazları ve Visual Studio makinesine doğrudan Ethernet kablosu ile bağlı olan herhangi bir cihazı görüntüler.

   **Bir C++ proje sayfasında uzak aygıtı belirtme**

   ![Uzaktan hata ayıklama için C&#43;&#43; proje özellikleri](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. **Başlatma** listesinden **Uzaktan hata ayıklayıcı** ' yı seçin.

8. **Makine adı** kutusuna uzak cihazın ağ adını girin. İsterseniz, uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusundan cihazı seçmek için kutudaki aşağı oku seçebilirsiniz.

   **Visual C# ve Visual Basic proje sayfasında uzak aygıtı belirtme**

   ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. **Hedef cihaz** listesinden **uzak makine** ' yi seçin.

10. Uzak cihazın ağ adını **uzak makine** kutusuna girin veya **bul** ' a tıklayarak **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusundan cihazı seçin.

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Dağıtım seçenekleri

Başlangıç projesinin hata ayıklama özelliği sayfasında aşağıdaki dağıtım seçeneklerini belirleyebilirsiniz.

**Ağ geri döngüsüne izin ver**

Güvenlik nedenleriyle, [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Standart biçimde yüklenen BIR UWP veya uygulamanın yüklü olduğu cihaza ağ çağrıları yapmasına izin verilmez. Visual Studio dağıtımı, varsayılan olarak, dağıtılan uygulama için bu kuraldan bir istisna oluşturur. Bu istisna, iletişim yordamlarını tek bir makinede test etmenizi sağlar. Uygulamanızı ' a göndermeden önce [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] , uygulamanızı muafiyet olmadan test etmelisiniz.

Uygulamadan ağ geri döngü muafiyetini kaldırmak için:

- C# ve Visual Basic hata ayıklama özelliği sayfasında, **ağ geri döngüsüne izin ver** onay kutusunu temizleyin.

- C++ hata ayıklama özelliği sayfasında, **ağ geri döngü değerini Izin ver** olarak **Hayır** olarak ayarlayın.

**başlatma, ancak başlatıldığında kodumun hatalarını ayıklama (C# ve Visual Basic)/uygulamayı başlatma (C++)**

Dağıtımı, uygulama başlatıldığında otomatik olarak bir hata ayıklama oturumu başlatacak şekilde yapılandırmak için:

- C# ve Visual Basic hata ayıklama özelliği sayfasında, **başlatılmayın ' i işaretleyin, ancak başladığında kodumdaki hata ayıkla** onay kutusunu işaretleyin.

- C++ hata ayıklama özelliği sayfasında, **Uygulamayı Başlat** değerini **Evet** olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş uzak dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md)
- [Visual Studio’dan uygulamaları çalıştırma](debugging-windows-store-and-windows-universal-apps.md)
