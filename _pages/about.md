---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<span class='anchor' id='about-me'></span>

[Dr. Hao Ding (丁豪)](https://facdent.hku.hk/about/staff-profile.php?shortname=haoding) is a postdoctoral fellow at Faculty of Dentistry, The University of Hong Kong (HKU), where he has been working since 2022. He earned his PhD in Dental Materials Science from HKU, where his research focuses on dental materials and digital dentistry. He has published more than 10 papers with a <a href='https://scholar.google.com/citations?user=pciroxQAAAAJ'> H-index of <strong><span id='total_cit'> 5
</span></strong></a>.

 <a href='https://scholar.google.com/citations?user=pciroxQAAAAJ'><img src="https://img.shields.io/endpoint?url={{ url | url_encode }}&logo=Google%20Scholar&labelColor=f6f6f6&color=9cf&style=flat&label=Citations"></a>

<style>
html, body, form, table, div, h1, h2, h3, h4, h5, h6, img, ol, ul, li, button {
    margin: 0px;
    padding: 0px;
    border: 0px none;
    color: #fff;
}

table {
    border-collapse: collapse;
    border-width: 0px;
    empty-cells: show;
}

body, td {
    font-size: 13px;
    font-family: Arial,sans-serif;
    line-height: 1.24;
}

.gsc_g_hist_wrp
{
	padding-top: 10px !important;
}

</style>

<?php  
	function filter_content($content, $url)
	{
		$contentText = '';
		$output = preg_match_all('/<div class="gsc_rsb_s gsc_prf_pnl" id="gsc_rsb_cit" role="region" aria-labelledby="gsc_prf_t-cit">(.*)<\/div><div class="gsc_rsb_s gsc_prf_pnl" id="gsc_rsb_co" role="region" aria-labelledby="gsc_prf_t-ath">/is',$content,$matches);
		// if this has not worked try another variant:
		if(!isset($matches[1][0]))
		{
		$output = preg_match_all('/<div class="gsc_rsb_s gsc_prf_pnl" id="gsc_rsb_cit" role="region" aria-labelledby="gsc_prf_t-cit">(.*)<\/div><div class="gsc_lcl" role="main" id="gsc_prf_w">/is',$content,$matches);
		}

		$contentText = isset($matches[1][0])?$matches[1][0]:'e1';

		preg_match_all('/Citations<\/a><\/td><td class="gsc_rsb_std">(\d+)<\/td>/is',$contentText,$matches);
		$citations = isset($matches[1][0])?$matches[1][0]:'e2';

		preg_match_all('/h-index<\/a><\/td><td class="gsc_rsb_std">(\d+)<\/td>/is',$contentText,$matches);
		$hindex = isset($matches[1][0])?$matches[1][0]:'e3';

		preg_match_all('/<style>(.+)/is',$contentText,$matches);
		$contentText2 = isset($matches[1][0])?$matches[1][0]:'e4';
 
		$contentText2 = '<style>'.$contentText2;

		$dom = new DOMDocument();
		$dom->preserveWhiteSpace = FALSE;
		$dom->loadHTML($contentText2);
		$dom->formatOutput = TRUE;

		$links = $dom->getElementsByTagName('a');

		//Loop through each <a> tags and replace them by their text content    
		for ($i = $links->length - 1; $i >= 0; $i--)
		{
			$linkNode = $links->item($i);
			$text = $linkNode->textContent;
			$style = $linkNode->getAttribute("style");
			$class = $linkNode->getAttribute("class");
			$div = $dom->createElement("div", $text);
			$div->setAttribute("class","$class");
			$div->setAttribute("style","$style");
			$linkNode->parentNode->replaceChild($div, $linkNode);
		}

		$contentText2 = $dom->saveHTML();
		$contentText2 = 'Citations according to <a href="'.$url.'">Google Scholar</a>: '
                                .$citations.' (h-index: '.$hindex.')'.$contentText2;
		
		return $contentText2; 
	}

	if($_GET["id"] != "" && $_GET["lang"] != "")
	{
		$curl = curl_init();

		$id = htmlspecialchars($_GET['id'], ENT_QUOTES, 'UTF-8');
		$lang = htmlspecialchars($_GET['lang'], ENT_QUOTES, 'UTF-8');
		$url = "http://scholar.google.de/citations?user=pciroxQAAAAJ&hl=en";

		curl_setopt($curl, CURLOPT_URL, $url);
		curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
		curl_setopt($curl, CURLOPT_FOLLOWLOCATION, 1);
		curl_setopt($curl, CURLOPT_CONNECTTIMEOUT, 60);

		print filter_content( curl_exec($curl), $url );
		#print curl_exec($curl);
	}
	else
	{
		print "ERROR: Cannot find Google Scholar Account </br>";
	}
?>

# 🔥 News
- *2024.05.06*: &nbsp;🎉🎉 My website officially launched.
 

# 📝 Publications 


-	Jiaojiao Yun, Michael F. Burrow, Jukka P. Matinlinna, **Hao Ding**, Rosalind S.M. Chan, James K.H. Tsoi, Yan Wang. Design of Multi-Functional Bio-Safe Dental Resin Composites with Mineralization and Anti-Biofilm Properties. *Journal of Functional Biomaterials*, 2024, 15(5): 120. (JCR:Q2; IF:4.8) [[HTML]](https://doi.org/10.3390/jfb15050120) [[PDF]](https://www.mdpi.com/2079-4983/15/5/120/pdf?version=1714482768)


- **Hao Ding**, Zeqian Pan, Yee-Man Loh, Chunjin Wang, James K.H. Tsoi. Effects of Nano-Diamond-Coated Milling Bits on Cutting Dental Zirconia. *Coatings*, 2024, 14(4): 473. (JCR:Q2; IF:3.4) [[HTML]](https://doi.org/10.3390/coatings14040473) [[PDF]](https://www.mdpi.com/2079-6412/14/4/473/pdf?version=1712929969)
<span class='show_paper_citations' data='pciroxQAAAAJ:_kc_bZDykSQC'></span>


- Yunzhen Yang, **Hao Ding**, Aifang Han, Xuedong Bai, Mohammed N. Bijle, Jukka P. Matinlinna, James K.H. Tsoi. *Porphyromonas gingivalis* can degrade dental zirconia. *Dental Materials*, 2023, 39(12): 1105-1112. (JCR:Q1; IF:5.0) [[HTML]](https://doi.org/10.1016/j.dental.2023.10.004)


- **Hao Ding**, Meng Zhang, Brian Lo, Karfield K.F. Chan, Edward C.M. Lo, James K.H. Tsoi. A Personalised 3D-Printed Dental Plaque Removal Mouthguard for Older Adults. *International Dental Journal*, 2023, 73(6): 828-833. (JCR:Q2; IF:3.3) [[HTML]](https://doi.org/10.1016/j.identj.2023.04.005) [[PDF]](https://www.sciencedirect.com/science/article/pii/S0020653923000722/pdfft?md5=85b8ecf07a47c928d5c183e2b8045595&pid=1-s2.0-S0020653923000722-main.pdf)


- **Hao Ding**, Zhiming Cui, Ebrahim Maghami, Yanning Chen, Jukka P. Matinlinna, Edmond H.N. Pow, Alex S.L. Fok, Michael F. Burrow, Wenping Wang, James K.H. Tsoi. Morphology and mechanical performance of dental crown designed by 3D-DCGAN. *Dental Materials*, 2023, 39(4): 320-332. (JCR:Q1; IF:5.0)
<img alt="Citation Badge" src="https://api.juleskreuer.eu/citation-badge.php?doi=10.1016/j.dental.2023.02.001">
[[HTML]](https://doi.org/10.1016/j.dental.2023.02.001) [[PDF]](https://www.sciencedirect.com/science/article/pii/S0109564123000416/pdfft?md5=2f702e181681eb353fab229989a81ac7&pid=1-s2.0-S0109564123000416-main.pdf)


- **Hao Ding**, Jiamin Wu, Wuyuan Zhao, Jukka P. Matinlinna, Michael F. Burrow, James K.H. Tsoi. Artificial intelligence in dentistry—A review. *Frontiers in Dental Medicine*, 2023, 4: 1085251.
<img alt="Citation Badge" src="https://api.juleskreuer.eu/citation-badge.php?doi=10.3389/fdmed.2023.1085251">
[[HTML]](https://doi.org/10.3389/fdmed.2023.1085251) [[PDF]](https://www.frontiersin.org/articles/10.3389/fdmed.2023.1085251/pdf?isPublishedV2=False)


# 🎖 Honors and Awards
- *2021.10* Under Construction. 

# 📖 Educations
- *2019.06 - 2022.04 (now)*, Under Construction 


<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=ffffff&w=300&t=n&d=VtuMTGPTkeAnHKKoDeGVhdPnIQXWl3H-5NAwHr0C6WY'></script>
