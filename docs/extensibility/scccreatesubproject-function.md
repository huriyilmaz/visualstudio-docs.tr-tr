---
description: Bu işlev, lpParentProjPath bağımsız değişkeni tarafından belirtilen var olan bir üst proje altında verilen ada sahip bir alt proje oluşturur.
title: Scccreatealt proje Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70568c27afb4bdb5794db64322113dffbd824452
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074008"
---
# <a name="scccreatesubproject-function"></a>Scccreatealt proje işlevi
Bu işlev, bağımsız değişken tarafından belirtilen mevcut bir üst proje altında verilen ada sahip bir alt proje oluşturur `lpParentProjPath` .

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpUser

[in, out] Kullanıcı adı (en fazla SCC_USER_SIZE, NULL Sonlandırıcı dahil).

 lpParentProjPath

'ndaki Üst projenin yolunu tanımlayan bir dize (NULL Sonlandırıcı dahil olmak üzere SCC_PRJPATH_SIZE kadar).

 lpSubProjName

'ndaki Önerilen alt proje adı (en fazla SCC_PRJPATH_SIZE, NULL Sonlandırıcı dahil).

 lpAuxProjPath

[in, out] Projeyi tanımlayan yardımcı dize (NULL Sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpSubProjPath

[in, out] Alt projenin yolunu tanımlayan çıkış dizesi (NULL Sonlandırıcı dahil olmak üzere SCC_PRJPATH_SIZE kadar).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Alt proje başarıyla oluşturuldu.|
|SCC_E_INITIALIZEFAILED|Üst proje başlatılamadı.|
|SCC_E_INVALIDUSER|Kullanıcı, kaynak denetimi sisteminde oturum açamadı.|
|SCC_E_COULDNOTCREATEPROJECT|Alt proje oluşturulamıyor.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje sözdizimi.|
|SCC_E_UNKNOWNPROJECT|Ana proje, kaynak denetimi eklentisi için bilinmiyor.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamayan dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_CONNECTIONFAILURE|Kaynak denetimi eklentisi bağlantı sorunu vardı.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Adında bir alt proje zaten varsa, işlev benzersiz bir tane oluşturmak için varsayılan adı değiştirebilir; Örneğin, buna "_ \<number> " ekleyerek. Çağıran,, ve üzerindeki değişiklikleri kabul etmek için hazırlanmalıdır `lpUser` `lpSubProjPath` `lpAuxProjPath` . `lpSubProjPath`Ve `lpAuxProjPath` bağımsız değişkenleri, [SccOpenProject](../extensibility/sccopenproject-function.md)çağrısında kullanılır. Bu, geri dönüş sırasında çağıran tarafından değiştirilmemelidir. Bu dizeler, kaynak denetimi eklentisinin bir projeyle ilişkilendirilmesi gereken bilgileri izlemek için bir yol sağlar. Çağıran IDE, bu iki parametreyi dönüşte görüntülemez, çünkü eklenti görüntülenmek için uygun olmayan bir biçimli dize kullanabilir. İşlev bir başarı veya hata kodu döndürür ve başarılı olursa, değişkeni `lpSubProjPath` yeni projenin tam proje yoluyla doldurur.

 Bu işlev, kullanıcının bir tane seçmesini istemek yerine sessizce bir proje oluşturması dışında, [SccGetProjPath](../extensibility/sccgetprojpath-function.md)öğesine benzerdir. `SccCreateSubProject`İşlev çağrıldığında ve boş olmaz ve `lpParentProjName` `lpAuxProjPath` geçerli bir projeye karşılık gelir. Bu dizeler genellikle, önceki `SccGetProjPath` işleve veya [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)'e YAPıLAN bir çağrıdan IDE tarafından alınır.

 `lpUser`Bağımsız değişken kullanıcı adıdır. IDE, daha önce aldığı Kullanıcı adına geçecek `SccGetProjPath` ve kaynak denetimi eklentisinin adı varsayılan olarak kullanması gerekir. Kullanıcının eklentiyle zaten açık bağlantısı varsa, eklentinin sessizce çalıştığından emin olmak için eklentinin herhangi bir istemi ortadan kaldırmaya çalışması gerekir. Ancak, oturum açma başarısız olursa, eklenti kullanıcıdan bir oturum açma isteği ister ve geçerli bir oturum açma bilgisi aldığında adı geri geçirin `lpUser` . Eklenti bu dizeyi değiştirebileceğinden, IDE her zaman bir boyut arabelleği ayırır (SCC_USER_LEN + 1 veya SCC_USER_SIZE, null Sonlandırıcı için boşluk içerir). Dize değiştirilirse, yeni dize geçerli bir oturum açma adı olmalıdır (en azından eski dize olarak geçerli olur).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Scccreatealt projesi ve SccGetParentProjectPath için teknik notlar
 Kaynak denetimine çözüm ve proje ekleme, bir kullanıcının kaynak denetim sisteminde konumları kaç kez seçmesi gerektiğini en aza indirmek için Visual Studio 'da basitleştirilmiştir. Bu değişiklikler, bir kaynak denetimi eklentisi hem yeni işlevleri hem de ' yi destekliyorsa, Visual Studio tarafından etkinleştirilir `SccCreateSubProject` `SccGetParentProjectPath` . Ancak, aşağıdaki kayıt defteri girişi, bu değişiklikleri devre dışı bırakmak ve önceki Visual Studio 'ya geri dönmek için kullanılabilir (kaynak denetimi eklentisi API sürümü 1,1) davranışı:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Bu kayıt defteri girdisi yoksa veya DWORD: 00000000 olarak ayarlandıysa, Visual Studio yeni işlevleri ve ' ı kullanmaya çalışır `SccCreateSubProject` `SccGetParentProjectPath` .

 Kayıt defteri girişi DWORD: 00000001 olarak ayarlandıysa, Visual Studio bu yeni işlevleri kullanmayı denemez ve kaynak denetimine ekleme işlemleri Visual Studio 'nun önceki sürümlerinde olduğu gibi çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
