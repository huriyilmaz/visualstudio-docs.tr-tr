---
title: 'Nasıl yapılır: projeleri hedef platformları için yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6ba899fd1b17fa5a82c64d5c5e44e67f0d5eb97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668198"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Nasıl Yapılır: Projeleri Hedef Platformlar İçin Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulamalarınızı, 64 bitlik platformlar dahil olmak üzere farklı platformları hedefleyecek şekilde ayarlamanıza olanak sağlar. Sürümünde 64 bit platform desteği hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bkz. [64-bit uygulamalar](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="targeting-platforms-with-the-configuration-manager"></a>Platformları Configuration Manager ile hedefleme
 **Configuration Manager** , projenizde hedeflemek üzere yeni bir platform eklemek için bir yol sağlar. İle dahil olan platformlardan birini seçerseniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , projenizin özellikleri seçili platform için projenizi oluşturmak üzere değiştirilir.

#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Bir projeyi 64 bitlik bir platformu hedefleyecek şekilde yapılandırmak için

1. Menü çubuğunda, **Configuration Manager** **Oluştur**' u seçin.

2. **Etkin çözüm platformu** listesinde, çözümün hedeflenecek 64 bitlik bir platform seçin ve sonra **Kapat** düğmesini seçin.

   1. İstediğiniz Platform **etkin çözüm platformu** listesinde görünmüyorsa, **Yeni**' yi seçin.

        **Yeni çözüm platformu** iletişim kutusu görüntülenir.

   2. **Yazın veya yeni platform listesini seçin** , **x64**öğesini seçin.

       > [!NOTE]
       > Yapılandırmanıza yeni bir ad verirseniz, **Proje tasarımcısında** ayarları doğru platformu hedefleyecek şekilde değiştirmeniz gerekebilir.

   3. Ayarları geçerli platform yapılandırmasından kopyalamak istiyorsanız, seçin ve sonra **Tamam** düğmesini seçin.

   64 bitlik platformu hedefleyen tüm projeler için özellikler güncellenir ve projenin sonraki derlemesi 64 bit platformlar için iyileştirilir.

## <a name="targeting-platforms-in-the-project-designer"></a>Proje tasarımcısında platformları hedefleme
 Proje Tasarımcısı Ayrıca, projenizle farklı platformları hedeflemek için bir yol sağlar. **Yeni çözüm platformu** iletişim kutusundaki listede yer alan platformlardan birini seçmek çözümünüz için çalışmazsa, özel bir yapılandırma adı oluşturabilir ve **Proje tasarımcısında** ayarları değiştirerek doğru platformu hedefleyebilirsiniz.

 Bu görevin gerçekleştirilmesi, kullanmakta olduğunuz programlama diline göre farklılık gösterir. Daha fazla bilgi için aşağıdaki bağlantılara bakın:

- [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Projeler için bkz. [/Platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

- [!INCLUDE[csprcs](../includes/csprcs-md.md)]Projeler için bkz. [derleme sayfası, proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).

- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Projeler için bkz. [/clr (ortak dil çalışma zamanı derlemesi)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme platformlarını anlama](../ide/understanding-build-platforms.md) [/Platform (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04) [64-bit uygulamalar](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181) [Visual Studio IDE 64-bit desteği](../ide/visual-studio-ide-64-bit-support.md)
