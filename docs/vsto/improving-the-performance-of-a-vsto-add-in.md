---
title: VSTO eklentisinin performansını iyileştirme
description: Office uygulamaları için oluşturduğunuz VSTO Eklentilerini, hızlı bir başlangıç, kapatma, öğeleri açma ve diğer görevleri gerçekleştirmeye yönelik olarak nasıl iyileştiriceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29035f4867421ed3f05e5f0c3a5c196f58b7ab34
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825127"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>VSTO eklentisinin performansını iyileştirme
  Office uygulamaları için oluşturduğunuz VSTO Eklentilerini en iyi duruma getirerek daha iyi bir deneyim verebilirsiniz. bu sayede, öğeleri hızlı bir şekilde başlatabilir, kapatabilir, açık öğeler açabilir ve diğer görevleri gerçekleştirebilirsiniz. VSTO eklentisi Outlook için ise, VSTO eklentisinin kötü performans nedeniyle devre dışı bırakılabilme olasılığını da azaltabilirsiniz. Aşağıdaki stratejileri uygulayarak VSTO eklentisinin performansını artırabilirsiniz:

- [İsteğe bağlı VSTO Eklentilerini yükleyin](#Load).

- [Windows Installer kullanarak Office çözümlerini yayımlayın](#Publish).

- [Şerit yansımasını atlayın](#Bypass).

- [Ayrı bir yürütme iş parçacığında pahalı Işlemler gerçekleştirin](#Perform).

  Outlook VSTO eklentisinin nasıl iyileştirileceği hakkında daha fazla bilgi için bkz. [VSTO Eklentilerini etkin tutmak Için performans ölçütleri](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a> VSTO Eklentilerini isteğe bağlı olarak yükle
 Bir VSTO eklentisini yalnızca aşağıdaki koşullarda yüklenecek şekilde yapılandırabilirsiniz:

- VSTO eklentisi yüklendikten sonra Kullanıcı uygulamayı ilk kez başlattığında.

- Uygulamanın, sonraki bir zamanda uygulama başladıktan sonra VSTO eklentisi ile ilk kez etkileşime geçtiğinde.

  Örneğin, Kullanıcı verilerimi **Al** etiketli özel bir düğme seçtiğinde VSTO eklentisi bir çalışma sayfasını verilerle doldurabilir. Uygulamanın, **veri al** düğmesinin şeritte GÖRÜNEBILMESI Için VSTO eklentisini en az bir kez yüklemesi gerekir. Ancak, Kullanıcı uygulamayı bir sonraki sefer başlattığında VSTO eklentisi yeniden yüklenmez. VSTO eklentisi yalnızca Kullanıcı verilerimi **Al** düğmesini seçtiğinde yüklenir.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>VSTO Eklentilerini isteğe bağlı olarak yüklemek üzere bir ClickOnce çözümü yapılandırmak için

1. **Çözüm Gezgini**, proje düğümünü seçin.

2. Menü çubuğunda,   >  **özellik sayfalarını** görüntüle ' yi seçin.

3. **Yayımla** sekmesinde **Seçenekler** düğmesini seçin.

4. **Yayımla Seçenekleri** Iletişim kutusunda **Office ayarları** liste öğesini seçin, **isteğe bağlı yükle** seçeneğini belirleyin ve **Tamam** düğmesini seçin.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>VSTO Eklentilerini isteğe bağlı olarak yüklemek üzere bir Windows Installer çözümü yapılandırmak için

1. Kayıt defterinde `LoadBehavior` **_kök_\Software\microsoft\office \\ _ApplicationName_\addıns \\ _eklenti kimliği_** anahtarının girdisini **0x10** olarak ayarlayın.

     Daha fazla bilgi için bkz. [VSTO eklentileri Için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Çözümde hata ayıklarken VSTO Eklentilerini isteğe bağlı olarak yüklemek üzere bir çözüm yapılandırmak için

1. `LoadBehavior` **_Kök_\Software\microsoft\office \\ _ApplicationName_\ eklentileri \\ _eklenti kimliği_** anahtarının **0x10**' a girişini ayarlayan bir betik oluşturun.

     Aşağıdaki kod bu betiğin bir örneğini gösterir.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Betiği kullanarak kayıt defterini güncelleştiren oluşturma sonrası bir olay oluşturun.

     Aşağıdaki kod, bir derleme sonrası olayına ekleyebileceğiniz komut dizesinin bir örneğini gösterir.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     C# projesinde oluşturma sonrası olay oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: derleme olaylarını belirtme &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Visual Basic projesinde oluşturma sonrası bir olay oluşturma hakkında bilgi için, bkz. [nasıl yapılır: derleme olaylarını belirtme &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a> Windows Installer kullanarak Office çözümlerini yayımlama
 Çözümünüzü Windows Installer kullanarak yayımlarsanız, Office çalışma zamanı için Visual Studio 2010 araçları, VSTO eklentisi yüklenirken aşağıdaki adımları atlar.

- Bildirim şeması doğrulanıyor.

- Güncelleştirmeler otomatik olarak denetleniyor.

- Dağıtım bildirimlerinin dijital imzaları doğrulanıyor.

  > [!NOTE]
  > Bu yaklaşım, VSTO eklentisini kullanıcıların bilgisayarlarındaki güvenli bir konuma dağıtırsanız gerekli değildir.

  Daha fazla bilgi için bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Şerit yansımasını atla
 Kullanarak bir çözüm oluşturursanız [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , çözüm dağıtırken kullanıcılarınızın Office çalışma zamanı Için Visual Studio 2010 araçları 'nın en son sürümünü yüklediğinizden emin olun. VSTO çalışma zamanının daha eski sürümleri, şerit özelleştirmelerini bulmak için çözüm derlemelerine yansıtılır. Bu işlem, VSTO eklentisinin daha yavaş yüklenmesine neden olabilir.

 Alternatif olarak, Office çalışma zamanı için Visual Studio 2010 araçlarının herhangi bir sürümünün, şerit özelleştirmelerini belirlemek için yansıma kullanmasını engelleyebilirsiniz. Bu stratejiyi takip etmek için yöntemini geçersiz kılın `CreateRibbonExtensibility` ve doğrudan şerit nesnelerini döndürün. VSTO eklentileriniz hiçbir Şerit özelleştirmesi içermiyorsa, `null` yönteminin içine dönün.

 Aşağıdaki örnek, bir alanın değerine göre bir şerit nesnesi döndürür.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs" id="Snippet1":::

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Ayrı bir yürütme iş parçacığında pahalı işlemler gerçekleştirme
 Ayrı bir iş parçacığında zaman alan görevler (uzun süre çalışan görevler, veritabanı bağlantıları veya diğer ağ çağrısı sayısı gibi) gerçekleştirmeyi göz önünde bulundurun. Daha fazla bilgi için bkz. [Office 'Te Iş parçacığı desteği](../vsto/threading-support-in-office.md).

> [!NOTE]
> Office nesne modeline çağıran tüm kodun ana iş parçacığında yürütülmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [VSTO eklentileri talep yükleme](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Office eklentilerinde CLR Yükleme gecikmesi](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Visual Studio kullanarak Office için VSTO Eklentileri oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md)