---
title: Windows Mağazası uygulamalarını dağıtma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177463"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Visual Studio’dan Microsoft Store uygulamaları dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")

 Visual Studio dağıtım işlevselliği, Visual Studio ile oluşturulan Windows Mağazası uygulamalarını bir hedef cihazda oluşturur ve kaydeder. Uygulamanın nasıl kaydedildiği, hedef cihazın yerel mi yoksa uzak mı olduğuna bağlıdır:

- Hedef, yerel Visual Studio makinesi olduğunda, Visual Studio uygulamayı Build klasöründen kaydeder.

- Hedef uzak bir cihaz olduğunda, Visual Studio gerekli dosyaları uzak makineye kopyalar ve uygulamayı bu cihaza kaydeder.

  Uygulamanızı Visual Studio 'dan hata **ayıklamayı Başlat** seçeneğini (klavye: F5) veya **hata ayıklama olmadan Başlat** SEÇENEĞINI (klavye: CTRL + F5) kullanarak yaptığınızda dağıtım otomatik olarak yapılır. Uygulamanızı el ile de dağıtabilirsiniz. Aşağıdaki senaryolarda el ile dağıtım yararlı olur:

- Yerel veya uzak bir makinede geçici test.

- Hata ayıklamak istediğiniz başka bir uygulamayı başlatacak bir uygulama dağıtma.

- Başka bir uygulama veya yöntem tarafından başlatıldığında Ayıklanacak bir uygulama dağıtma.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 Bu konu başlığında şunları öğrenebilirsiniz:

 [Windows Mağazası uygulaması dağıtma](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Uzak cihaz belirtme](#BKMK_How_to_specify_a_remote_device)

 [Dağıtım seçenekleri](#BKMK_Deployment_options)

## <a name="how-to-deploy-a-windows-store-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Windows Mağazası uygulaması dağıtma
 Uygulamayı el ile dağıtmak basit bir işlemdir:

1. Uzak bir cihaza dağıtıyorsanız, uygulamanın başlangıç projesinin Özellik projesi sayfasında cihazın adını veya IP adresini belirtin. (Bunu yapmak için adımlar bu konuda daha sonra listelenmiştir.).

2. Hata ayıklayıcı Visual Studio araç çubuğunda, **hata ayıklamayı Başlat** düğmesinin yanındaki açılan listeden dağıtım hedefini seçin.

     ![Yerel makinede Çalıştır](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. **Yapı** menüsünde **Dağıt** ' ı seçin.

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Uzak cihaz belirtme
 **Önkoşullar**

 Bir uygulamayı uzak bir cihaza dağıtmak için:

- Bir geliştiricinin lisansının uzak cihaza yüklenmesi gerekir.

- Visual Studio uzak araçları uzak cihaza yüklenmeli ve Uzaktan Hata Ayıklama İzleyicisi çalışıyor olmalıdır.

     Dağıtım, uzak cihaza uygulama dosyalarını göndermek için uzaktan hata ayıklayıcı ağ kanalını kullanır.

#### <a name="to-specify-a-remote-device"></a>Uzak bir cihaz belirtmek için

1. Başlangıç projesinin hata ayıklama özelliği sayfasında, uzak dağıtım hedefinin adını veya IP adresini belirtin.

2. Hata ayıklama özelliği sayfasını açmak için Çözüm Gezgini ' de projeyi seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

3. Sonra özellik sayfaları penceresinde **hata ayıklama** düğümünü seçin.

4. Uzak cihazın adını veya IP adresini yazabilir veya cihazı **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusundan seçebilirsiniz.

    ![Uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu, yerel ağ alt ağındaki ve bir Ethernet kablosu tarafından doğrudan Visual Studio makinesine bağlı olan tüm cihazlardan cihazları görüntüler.

   **Uzak aygıtı bir JavaScript veya Visual C++ projesi sayfasında belirtme**

   ![Uzaktan hata ayıklama için C&#43;&#43; proje özellikleri](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. **Başlatma** listesinden **Uzaktan hata ayıklayıcı** ' yı seçin.

6. **Makine adı** kutusuna uzak cihazın ağ adını girin. İsterseniz, uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusundan cihazı seçmek için kutudaki aşağı oku seçebilirsiniz.

   **Visual C# ve Visual Basic proje sayfasında uzak aygıtı belirtme**

   ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. **Hedef cihaz** listesinden **uzak makine** ' yi seçin.

8. Uzak cihazın ağ adını **uzak makine** kutusuna girin veya **bul** ' a tıklayarak **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusundan cihazı seçin.

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Dağıtım seçenekleri
 Başlangıç projesinin hata ayıklama özelliği sayfasında aşağıdaki dağıtım seçeneklerini belirleyebilirsiniz.

 **Ağ geri döngüsüne Izin ver** Güvenlik nedenleriyle, [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Standart biçimde yüklenen bir uygulamanın, üzerinde yüklü olduğu cihaza ağ çağrıları yapmasına izin verilmez. Varsayılan olarak, Visual Studio dağıtımı, dağıtılan uygulama için bu kuraldan bir istisna oluşturur. Bu istisna, iletişim yordamlarını tek bir makinede test etmenizi sağlar. Uygulamanızı ' a göndermeden önce [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] , uygulamanızı muafiyet olmadan test etmelisiniz.

 Uygulamadan ağ geri döngü muafiyetini kaldırmak için:

- C# ve VB hata ayıklama özelliği sayfasında, **ağ geri döngüsüne Izin ver** onay kutusunu temizleyin.

- JavaScript ve hata ayıklama özelliği sayfasında, **ağ geri döngü değerini Izin ver** ' i **Hayır**olarak ayarlayın.

  **Başlatma, ancak başlatıldığında kodumdaki hata ayıkla (C# ve vb)/uygulamayı Başlat (JavaScript ve C++)** Dağıtımı, uygulama başlatıldığında otomatik olarak bir hata ayıklama oturumu başlatacak şekilde yapılandırmak için:

- C# ve VB hata ayıklama özellik sayfasında, **başlatılmayın ' i işaretleyin, ancak başladığında kodumdaki hata ayıkla** onay kutusunu işaretleyin.

- JavaScript ve hata ayıklama özelliği sayfasında, **Uygulamayı Başlat** değerini **Evet**olarak ayarlayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio’dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md)
