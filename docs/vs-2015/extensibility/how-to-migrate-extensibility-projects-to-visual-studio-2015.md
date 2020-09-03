---
title: "Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2015 'ye geçirme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2f4926a503304491164635b983353ba7f3bb0f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75915979"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Nasıl Yapılır: Genişletilebilirlik Projelerini Visual Studio 2015’e Geçirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantınızı nasıl yükselteceğiniz aşağıda verilmiştir.  
  
> [!IMPORTANT]
> Visual Studio 'nun önceki bir sürümü için uzantı çözümünüzün bir sürümünü korumak istiyorsanız, ' yi yükseltmeden önce bir kopya yaptığınızdan emin olun. Yükseltilen sürümü önceki durumuna döndürmek zor olabilir.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Bir genişletilebilirlik çözümünü yükseltmek için  
  
1. Yükseltmek istediğiniz kopyayı kullanarak yeni sürümde açın. Yükseltmenin geri alınamaz olması tavsiye edilir.  
  
2. Yükseltme tamamlandıktan sonra dış programın yolunu yeni devenv.exe sürümüne değiştirin. **Çözüm Gezgini**proje düğümüne sağ tıklayın ve ardından **Özellikler**' i seçin. **Hata Ayıkla** sekmesinde, **dış program Başlat** ' ı seçerek metin kutusunu bulun ve devenv.exe yolunu Visual Studio 2015 yoluyla değiştirin, bu da şuna benzer bir şekilde görünmelidir:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3. Microsoft.VisualStudio.Shell.14.0.dll bir başvuru ekleyin. ( **Çözüm Gezgini** proje düğümüne sağ tıklayın ve ardından **Ekle/başvur**' ı seçin. **Uzantılar** sekmesini seçin ve ardından **Microsoft. VisualStudio. Shell. 14.0**.) öğesini kontrol edin.  
  
4. Çözümü derleyin. Oluşturulan dosyalar şu şekilde dağıtılır:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions \\<yazar adı \> \\<proje adı \> \\<proje sürümü \> \\ **.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Bir genişletilebilirlik projesini NuGet VS SDK başvuru Derlemeleriyle güncelleştirmek için  
  
1. Projenizin ihtiyaç duyacağı VS SDK başvuru derlemelerini belirleme.  **Çözüm Gezgini**, projenin **Başvurular** düğümünü genişletin ve proje başvuruları listesini gözden geçirin.  VS SDK başvuruları derlemeler, adında **Microsoft. VisualStudio** ön ekine sahip olur (örneğin: Microsoft. VisualStudio. Shell. 14.0).  
  
2. VS SDK başvuru derlemelerini projeden seçerek kaldırın, sağ tıklayın ve **kaldırın**.  
  
3. VS SDK başvuru derlemelerinin NuGet sürümlerini ekleyin.  Hala **Çözüm Gezgini başvurular** düğümünde, **NuGet Paketlerini Yönet...** öğesini açın. iletişim.  Bu iletişim kutusu hakkında daha fazla bilgi edinmek istiyorsanız, bkz. [Iletişim kutusunu kullanarak NuGet paketlerini yönetme](/nuget/consume-packages/install-use-packages-visual-studio). VS SDK başvuru derlemeleri [NuGet.org](https://www.nuget.org/) tarafından [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility)tarafından yayımlanır.  
  
4. **Paket kaynağınız**olarak **NuGet.org** kullanarak, Istenen başvuru derlemesiyle eşleşen NuGet paket adını arayın (örneğin: Microsoft. VisualStudio. Shell. 14.0) ve bunu projenize yükler.  NuGet, ilk derlemenin bağımlılıklarını karşılamak için birden çok başvuru derlemesi ekleyebilir.  
  
     İsterseniz, VS SDK [meta paketini](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)yükleyerek tüm vs SDK başvuru derlemelerini tek seferde ekleyebilirsiniz.  
  
5. VS SDK derleme araçlarının NuGet sürümünü kullanarak da geçiş yapabilirsiniz. Bu NuGet paketi [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) ve projenize eklendikten sonra, vs SDK yüklü olmayan bir bilgisayarda genişletilebilirlik projenizi oluşturmanızı sağlamak için gerekli araçları ve hedef dosyaları içerir.  
  
> [!NOTE]
> NuGet başvuru derlemelerini ve araçlarını kullanmak için mevcut genişletilebilirlik projelerinizi güncelleştirmeniz gerekmez.  VS SDK ile yüklenen başvuru derlemeleri ve araçları kullanarak oluşturmaya devam edebilirler.
