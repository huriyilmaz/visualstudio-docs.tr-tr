---
title: 'Nasıl yapılır: Visual Studio çözümünün bir parçası değil yürütülebilir dosya hatalarını ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e33233fd313cd6a73013ce55333a860663ddb601
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704518"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Nasıl Yapılır: Visual Studio Çözümünün Parçası Olmayan Yürütülebilir Öğede Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen, bir projenin parçası olmayan bir çalıştırılabilirin hatalarını ayıklamak isteyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dışında oluşturduğunuz bir yürütülebilir dosya veya başka bir kişiden aldığınız bir yürütülebilir dosya olabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Bu sorunun her zamanki yanıtı, yürütülebilir dosyayı Visual Studio dışında başlatmak ve hata ayıklayıcıyı kullanarak buna eklemektir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz.[çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Bir uygulamaya eklemek için bazı el ile adımlar gerekir, bu nedenle birkaç saniye sürer. Bu hafif gecikme, başlangıç sırasında oluşan bir sorunu ayıklamaya çalışıyorsanız iliştirme işleminin yardımcı olmayacağı anlamına gelir. Ayrıca, Kullanıcı girişini beklememe ve hızlı bir şekilde sona ermediği bir programda hata ayıklaması yapıyorsanız, buna iliştirmek için zaman açamayabilirsiniz. [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Yüklüyse, böyle bir program için BIR exe projesi oluşturabilirsiniz.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Mevcut bir yürütülebilir dosya için bir EXE projesi oluşturmak için  
  
1. **Dosya** menüsünde **Aç** ' a tıklayın ve **Proje**' yi seçin.  
  
2. **Proje Aç** iletişim kutusunda, **dosya adı** kutusunun yanındaki aşağı açılan listeye tıklayın ve **tüm proje dosyaları**' nı seçin.  
  
3. Yürütülebilir dosyayı bulun ve **Tamam**' a tıklayın.  
  
     Bu, yürütülebilir dosyayı içeren geçici bir çözüm oluşturur.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Bir yürütülebilir dosyayı bir Visual Studio çözümüne aktarmak için  
  
1. **Dosya** menüsünde **Proje Ekle**' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın.  
  
2. **Varolan Proje Ekle** iletişim kutusunda, **dosya adı** kutusunun yanındaki aşağı açılan listeye tıklayın ve **tüm proje dosyaları**' nı seçin.  
  
3. Yürütülebilir dosyayı bulun ve seçin.  
  
4. **Tamam**’a tıklayın.  
  
5. **Hata Ayıkla** menüsünden **Başlangıç**gibi bir yürütme komutu seçerek yürütülebilir dosyayı başlatın.  
  
    > [!NOTE]
    > Tüm programlama dilleri EXE projelerini desteklemez. [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Bu özelliği kullanmanız gerekiyorsa, ' i yükleyebilirsiniz.  
  
     Kaynak kodu olmadan bir yürütülebilir dosyada hata ayıklaması yaparken, kullanılabilir hata ayıklama özellikleri sınırlı olarak çalışır, çalışan bir çalıştırılabilire iliştirilip veya yürütülebilir dosyayı bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüme eklemektir. Yürütülebilir dosya, uyumsuz bir biçimde hata ayıklama bilgileri olmadan oluşturulduysa, kullanılabilir özellikler daha fazla sınırlıdır. Kaynak kodunuz varsa, en iyi yaklaşım kaynak kodu içine aktarmak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve içinde yürütülebilir dosyanın hata ayıklama derlemesini oluşturmaktır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [DBG dosyaları](https://msdn.microsoft.com/91e449e9-8b65-4123-960f-2107cd1f1cfd)
