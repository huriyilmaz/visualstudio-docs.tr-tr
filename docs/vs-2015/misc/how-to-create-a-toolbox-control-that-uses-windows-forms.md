---
title: 'Nasıl yapılır: Windows Forms kullanan bir araç kutusu denetimi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: 8436b8eee0193715e4ae886db18f91f7148dcb3b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300421"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Nasıl yapılır: Windows Forms kullanan bir araç kutusu denetimi oluşturma
[!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] eklenen Windows Forms araç kutusu denetim şablonu, uzantı yüklendiğinde **araç kutusuna** otomatik olarak eklenen Windows Forms denetimleri oluşturmanıza imkan tanır. Bu konu başlığı altında, diğer kullanıcılara dağıtabileceğiniz bir **araç kutusu** denetimi oluşturmak için şablonunun nasıl kullanılacağı gösterilmektedir.  
  
> [!NOTE]
> Visual Studio SDK 'sını nasıl indirecek hakkında bilgi edinmek için MSDN Web sitesinde [Visual Studio genişletilebilirlik Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=121964) ' ne bakın.  
  
## <a name="creating-a-toolbox-control"></a>Araç kutusu denetimi oluşturma  
 Projeyi oluşturmak için Windows Forms araç kutusu denetim şablonunu kullanın ve ardından Tasarımcıda bir kullanıcı arabirimi (UI) oluşturun.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Windows Forms araç kutusu denetimi projesi oluşturmak için  
  
1. **Dosya** menüsünde **Yeni**' ye ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**' ın altında, tercih ettiğiniz programlama dilinin düğümüne tıklayın ve ardından **genişletilebilirlik**' e tıklayın. Proje türleri listesinde **Windows Forms araç kutusu denetimi**' ni seçin.  
  
3. **Ad** kutusuna proje için kullanmak istediğiniz adı yazın. **Tamam**'a tıklayın.  
  
     Visual Studio, bir kullanıcı denetimi, denetimin **araç kutusuna**yerleştirilecek bir öznitelik ve dağıtım IÇIN bir VSIX bildirimi içeren bir çözüm oluşturur.  
  
#### <a name="to-build-the-control-ui"></a>Denetim Kullanıcı arabirimini oluşturmak için  
  
1. **Çözüm Gezgini**, tasarımcıda açmak için ToolboxControl.cs öğesine çift tıklayın.  
  
2. **Araç kutusundan**istediğiniz denetimleri tasarım yüzeyine sürükleyin ve tasarımınıza göre düzenleyin.  
  
3. **Özellikler** penceresinde, Kullanıcı denetimindeki ve alt denetimlerde ortak özellikleri ayarlayın.  
  
## <a name="coding-the-control"></a>Denetimi kodlama  
 Varsayılan olarak, denetiminiz, çözümünüzde aynı ada sahip bir **araç kutusu** öğe grubunda **ToolboxControl1** olarak **araç kutusunda** görünür. ToolboxControl.cs dosyasında bu adları değiştirebilirsiniz.  
  
#### <a name="to-code-the-control"></a>Denetimi kodlayın  
  
1. **Çözüm Gezgini**' de, ToolboxControl.cs ' a sağ tıklayın ve ardından kodu **görüntüle** ' ye tıklayarak dosyayı kod görünümünde açın.  
  
2. Denetimi uygulayan kısmi sınıfın tanımında sınıf adına sağ tıklayın, yeniden **Düzenle**' ye ve ardından **Yeniden Adlandır**' a tıklayın. Sınıf adını, denetim yüklendiğinde **araç kutusunda** görüntülenmesini istediğiniz adla değiştirin.  
  
3. Sınıf tanımının hemen üstünde, `ProvideToolboxControl` Attribute bildiriminde, ilk parametrenin değerini **araç kutusunda**denetimi barındıracak olan öğe grubunun adıyla değiştirin.  
  
     Aşağıdaki örnek, `General` öğesi grubunda `Counter` adlı bir denetim için `ProvideToolboxControl` özniteliğini ve ayarlanmış sınıf tanımını gösterir.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4. Denetim için özellikleri, yöntemleri ve olayları uygulayın.  
  
## <a name="building-testing-and-deployment"></a>Oluşturma, test etme ve dağıtma  
 F5 tuşuna basıldığında. vsix dağıtım dosyası içeren proje oluşturulur ve **araç kutusu**'nda yüklü olan Ikinci bir Visual Studio örneği açılır.  
  
#### <a name="to-build-and-test-the-control"></a>Denetimi derlemek ve test etmek için  
  
1. F5 tuşuna basın.  
  
2. Visual Studio 'nun yeni örneğinde bir Windows Forms uygulama projesi oluşturun.  
  
3. **Araç kutusu** 'nda denetiminizi bulun ve tasarım yüzeyine sürükleyin.  
  
4. **Özellikler** penceresinde, özelliklerinizi beklenen şekilde göründüğünü doğrulayın.  
  
5. Yöntemlerinizi ve olaylarınızı test etmek için gereken tüm kod veya ek denetimleri ekleyin.  
  
6. Windows Forms uygulamasını açmak için F5 tuşuna basın.  
  
7. Denetiminizin özelliklerinin, yöntemlerinin ve olaylarının beklendiği gibi davrandığını doğrulayın.  
  
#### <a name="to-deploy-the-control"></a>Denetimi dağıtmak için  
  
1. Test edilmiş projeyi oluşturduktan sonra, dosya Gezgini 'nde projenin \bin\debug\ klasörünü açın ve. vsix dosyasını bulun.  
  
2. . Vsix dosyasını bir ağa veya bir Web sitesine yükleyin.  
  
     Dosyayı [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine yüklerseniz, diğer kullanıcılar denetimi bulmak ve yüklemek Için Visual Studio 'Daki **Uzantı Yöneticisi 'ni** kullanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Araç Kutusu Denetimi Oluşturma](../extensibility/creating-a-wpf-toolbox-control.md)