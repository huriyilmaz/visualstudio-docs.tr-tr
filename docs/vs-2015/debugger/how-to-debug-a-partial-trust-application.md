---
title: 'Nasıl yapılır: kısmi güven uygulamasında hata ayıklama | Microsoft Docs'
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
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704481"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Nasıl Yapılır: Kısmen Güvenilen Uygulamada Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve konsol uygulamaları için geçerlidir.  
  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md) , bir makinedeki kaynaklara erişimi sınırlandırmak Için [kod erişim güvenliği](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) avantajlarından yararlanan kısmi güven uygulamalarının dağıtılmasını kolaylaştırır.  
  
 Kısmi güven uygulamalarının hata ayıklaması zor olabilir, çünkü kısmi güven uygulamaları farklı güvenlik izinlerine sahiptir (ve bu nedenle farklı davranır). İnternet 'ten yüklüyse, kısmi bir güven uygulaması birkaç izne sahip olur. Yerel intranetten yüklüyse, daha fazla izne sahip olur ve yerel bilgisayardan yüklüyse, tam izinleri olur. Özel izinlerle özel bölgelere de sahip olabilirsiniz. Bu koşulların herhangi birinde veya tümünde kısmi güven uygulamasında hata ayıklaması yapmanız gerekebilir. Neyse ki Visual Studio bu kadar kolay hale gelir.  
  
 Visual Studio 'da bir hata ayıklama oturumuna başlamadan önce, ' den yüklenen bir uygulamanın benzetimini yapmak istediğiniz bölgeyi seçebilirsiniz. Hata ayıklamayı başlattığınızda, uygulama ilgili bölgeden yüklenen kısmi güven uygulamasına uygun izinlere sahip olur. Bu, uygulamanın bu bölgeden indirilen bir kullanıcıya göründüğü şekilde davranışını görmenizi sağlar.  
  
 Uygulama, izni olmayan bir eylem gerçekleştirmeye çalışırsa, bir özel durum oluşur. Bu noktada, özel durum Yardımcısı, sorunu önlemek için gerekli izinlere sahip hata ayıklama oturumunu yeniden başlatmanızı sağlayan ek bir izin ekleme şansı sağlar.  
  
 Daha sonra geri dönüp hata ayıklama sırasında eklediğiniz izinleri görebilirsiniz. Hata ayıklama sırasında bir izin eklemeniz gerekiyorsa, büyük olasılıkla kodunuzda bu noktada bir Kullanıcı onay Istemi eklemeniz gerektiğini gösterir.  
  
> [!NOTE]
> Hata ayıklayıcı Görselleştiriciler kısmi güven uygulaması tarafından izin verilenden daha fazla ayrıcalık gerektiriyor. Kısmi güvenle kodda durdurulduğunda, Görselleştiriciler yüklenmez. Görselleştirici kullanarak hata ayıklamak için, kodu tam güvenle çalıştırmanız gerekir.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Kısmi güven uygulamanız için bir bölge seçmek üzere  
  
1. **Proje** menüsünde, _ProjectName_**Özellikler**' i seçin.  
  
2. *ProjectName* özellik sayfalarında **güvenlik** sayfasına tıklayın.  
  
3. **ClickOnce güvenlik ayarlarını etkinleştir**' i seçin.  
  
4. **Uygulamanızın yükleneceği bölge**bölümünde, açılan liste kutusuna tıklayın ve üzerinde yüklenmekte olan uygulamanın benzetimini yapmak istediğiniz bölgeyi seçin.  
  
     **Uygulama Kılavuzu için gereken izinler** , tüm kullanılabilir izinleri gösterir. Onay işareti, uygulamanıza verilen izinleri belirtir.  
  
5. Seçtiğiniz bölge **(özel)** Ise, **izinler** kılavuzunun **ayar** sütununda doğru özel ayarları seçin.  
  
6. Özellik sayfalarını kapatmak için **Tamam** ' ı tıklatın.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Bir güvenlik özel durumu oluştuğunda ek izin eklemek için  
  
1. **Özel durum Yardımcısı** iletişim kutusu şu iletiyle görüntülenir: **SecurityException işlenmedi.**  
  
2. **Özel durum Yardımcısı** iletişim kutusunda, **Eylemler**altında, **projeye izin Ekle**' ye tıklayın.  
  
3. **Hata ayıklamayı yeniden Başlat** iletişim kutusu görüntülenir.  
  
    - Hata ayıklama oturumunu yeni izinle yeniden başlatmak istiyorsanız **Evet**' e tıklayın.  
  
    - Henüz yeniden başlatmak istemiyorsanız **Hayır**' a tıklayın.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Hata ayıklama sırasında eklenen ek izinleri görüntülemek için  
  
1. **Proje** menüsünde, _ProjectName_**Özellikler**' i seçin.  
  
2. *ProjectName* özellik sayfalarında **güvenlik** sayfasına tıklayın.  
  
3. **Uygulama Kılavuzu için gereken izinlere** bakın. Eklediğiniz herhangi bir ek izin, eklenen sütunda iki simgeye sahiptir **: dahil edilen** tüm izinlere sahip olan normal onay işareti ve "i" harfini içeren bir balon gibi görünen ek bir simge.  
  
4. Uygulama Kılavuzu için **gereken tüm izinleri** görüntülemek için dikey kaydırma çubuğunu kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
