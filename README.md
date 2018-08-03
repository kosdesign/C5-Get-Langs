# C5-Get-Langs
Get all langs - link, text, local, icon

$locales = Site::getSite()->getLocales();

foreach($locales as $locale){
	$localeSiteTree = $locale->getSiteTree();
	$home = $localeSiteTree === null ? null : $localeSiteTree->getSiteHomePageObject();
	$loc = explode("_", $locale->getLocale());
  
  // check active lang
  $isActive = Localization::activeLocale()==$locale->getLocale() ? ' class="active"' : '';
  // icon
  $icon = '<img src="/concrete/images/countries/'.strtolower($loc[1]).'.png" />';
  // Full text => English
  $langText = $locale->getLanguageText();
  // Lang code => en
  $langCode = $locale->getLanguage();
  // Local code => en_GB
  $localCode = $locale->getLocale();
  // Home link
  $homeLink = $home->getCollectionLink();
}
