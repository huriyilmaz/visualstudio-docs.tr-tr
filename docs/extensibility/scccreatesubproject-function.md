---
description: Bu işlev, lpParentProjPath bağımsız değişkeni tarafından belirtilen mevcut bir üst proje altında verilen adla bir alt proje oluşturur.
title: SccCreateSubProject İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4f108439082152627024666e0bcd3b751e1d88d221e308de6f50767ca1d5c49c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305184"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject işlevi
Bu işlev, bağımsız değişkeni tarafından belirtilen mevcut bir üst proje altında verilen adla bir alt proje `lpParentProjPath` oluşturur.

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
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpUser

[in, out] Kullanıcı adı (NULL SCC_USER_SIZE dahil olmak üzere en fazla bir kullanıcı adı).

 lpParentProjPath

[in] Üst projenin yolunu tanımlayan dize (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpSubProjName

[in] Önerilen alt proje adı (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpUxProjPath

[in, out] Projeyi tanımlayan yardımcı dize (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpSubProjPath

[in, out] Alt proje yolunu tanımlayan çıkış dizesi (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Alt proje başarıyla oluşturuldu.|
|SCC_E_INITIALIZEFAILED|Üst proje başlatılamadı.|
|SCC_E_INVALIDUSER|Kullanıcı kaynak denetim sisteminde oturum açamdı.|
|SCC_E_COULDNOTCREATEPROJECT|Alt proje oluşturulamaz.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje söz dizimi.|
|SCC_E_UNKNOWNPROJECT|Üst proje, kaynak denetimi eklentisi tarafından bilinmiyor.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamaz dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişirken büyük olasılıkla ağ veya iletişim sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_CONNECTIONFAILURE|Kaynak denetimi eklentisi bağlantı sorunu vardı.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Adına sahip bir alt proje zaten varsa, işlev varsayılan adı değiştirerek benzersiz bir proje oluşturabilir, örneğin buna "_ \<number> " ekleyerek. Çağıranın , ve değişikliklerini kabul `lpUser` etmeye `lpSubProjPath` hazır olması `lpAuxProjPath` gerekir. Ardından `lpSubProjPath` `lpAuxProjPath` ve bağımsız değişkenleri [SccOpenProject çağrısında kullanılır.](../extensibility/sccopenproject-function.md) Bunlar, dönüş sırasında çağıran tarafından değiştirilmemelidir. Bu dizeler, kaynak denetimi eklentisinin bir projeyle ilişkilendirmek için gereken bilgileri izlemesi için bir yol sağlar. Eklenti görüntülemeye uygun olmayan biçimlendirilmiş bir dize kullanabileceği için çağıran IDE, dönüşte bu iki parametreyi görüntülemez. İşlev bir başarı veya hata kodu döndürür ve başarılı olursa değişkeni yeni projenin `lpSubProjPath` tam proje yoluyla doldurur.

 Bu işlev [SccGetProjPath](../extensibility/sccgetprojpath-function.md)işlevine benzer ancak kullanıcıdan birini seçmesini değil sessiz bir şekilde bir proje oluşturur. İşlev `SccCreateSubProject` çağrıldı mı, `lpParentProjName` boş olmaz ve geçerli bir projeye karşılık `lpAuxProjPath` gelecektir. Bu dizeler genellikle IDE tarafından işleve veya `SccGetProjPath` [SccGetParentProjectPath'e](../extensibility/sccgetparentprojectpath-function.md)yapılan önceki bir çağrıdan alınmıştır.

 bağımsız `lpUser` değişkeni kullanıcı adıdır. IDE daha önce kaynağından aldığı kullanıcı adını iletir ve kaynak denetimi eklentisi `SccGetProjPath` varsayılan olarak bu adı kullanmalıdır. Kullanıcının eklentiyle açık bir bağlantısı varsa, işlevin sessizce çalışmasını sağlamak için eklenti tüm istemleri ortadan kaldırmayı denemeli. Ancak, oturum açma başarısız olursa, eklenti kullanıcıdan oturum açma isteminde olmalı ve geçerli bir oturum açma bilgileri aldığında adı 'ye geri `lpUser` iletir. Eklenti bu dizeyi değiştirene kadar, IDE her zaman boyut arabelleği ayırır (null sonlandırıcı için alan içeren SCC_USER_LEN+1 veya SCC_USER_SIZE). Dize değiştirilirse, yeni dize geçerli bir oturum açma adı olmalıdır (en azından eski dize kadar geçerli).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject ve SccGetParentProjectPath için teknik notlar
 Kaynak denetimine çözüm ve proje ekleme işlemi Visual Studio kullanıcıdan kaynak denetim sisteminde konum seçmesi istendiğinde sayısını en aza indirmek için basitleştirildi. Kaynak denetimi eklentisi hem Visual Studio hem de 'i destekliyorsa, bu değişiklikler kaynak tarafından `SccCreateSubProject` `SccGetParentProjectPath` etkinleştirilir. Ancak, aşağıdaki kayıt defteri girdisi bu değişiklikleri devre dışı bırakmak ve önceki Visual Studio (Kaynak Denetimi Eklentisi API'si Sürüm 1.1) davranışına geri dönmek için kullanılabilir:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Bu kayıt defteri girdisi yoksa veya dword:00000000 olarak ayarlanırsa, Visual Studio ve işlevlerini kullanmayı `SccCreateSubProject` `SccGetParentProjectPath` denemez.

 Kayıt defteri girdisi dword:00000001 olarak ayarlanırsa, Visual Studio bu yeni işlevleri kullanmaya çalışmaz ve kaynak denetimine ekleme işlemleri önceki Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
