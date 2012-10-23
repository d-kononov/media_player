media_player
============

changed jw player v4.4 with streaming webcam+audio over rtmp

How to use this player to stream webcam+audio via wowza:

## Player parametrs

Inject this code to html page:

	<html lang="en">
	  <head>
		<script src="swfobject.js"></script>
		<script type="text/javascript">
		  var flashvars =
		  {
		    'streamer':                     'rtmp://xxx.xxx.xxx.xxx/live',
		    'file':                         'webcam.stream',
		    'type':                         'camera',
		    'controlbar':                   'bottom',
		    'stretching':                   'none',
		    'frontcolor':                   '86C29D',  // text & icons                  (green)
		    'backcolor':                    '849BC1',  // playlist background           (blue)
		    'lightcolor':                   'C286BA',  // selected text/track highlight (pink)
		    'screencolor':                  'FFFFFF',  // screen background             (black)
		    'id':                           'playerID',
		    'autostart':                    'true'
		  };

		  var params =
		  {
		    'allowfullscreen':              'true',
		    'allowscriptaccess':            'always',
		    'bgcolor':                      '#FFFFFF'
		  };

		  var attributes =
		  {
		    'id':                           'playerID',
		    'name':                         'playerID'
		  };
		  swfobject.embedSWF('player.swf', 'player', '320', '260', '9.0.124', false, flashvars, params, attributes);
		</script>
	  </head>
	  <body>
		<div id="playercontainer" class="playercontainer"><a id="player" class="player" href="http://get.adobe.com/flashplayer/">Get the Adobe Flash Player to see this video.</a></div>
	  </body>
	</html> 

## Wowza live streaming

Enable live streaming plugin in wowza. 
Create webcam.stream file in content wowza folder with next content:

rtmp://xxx.xxx.xxx.xxx/live/livestream

## Get stream

Create player html file with below content, or open wowza example page (live.html) and play rtmp://xxx.xxx.xxx.xxx/live/ with webcam.stream stream.

	<html>
	<head>
	<script type='text/javascript' src='jwplayer.js'></script>
	</head>
	<body>
	<div id='mediaspace'>This text will be replaced</div>
	<script type='text/javascript'>
	  jwplayer('mediaspace').setup({
		'flashplayer': 'player.swf',
		'type': 'rtmp',
		'streamer': 'rtmp://xxx.xxx.xxx.xxx/live',
		'autostart': 'true',
		'bufferlength': '3,
		'file': 'webcam.stream',
		'controlbar': 'none',
		'width': '320',
		'height': '260'
	  });
	</script>
	</body>
	</html>

## License

All html code was taken from http://foxpa.ws/2011/10/27/stream-webcams-and-sound-in-flash-via-rtmp-with-jw-player/

I've copied jw player project and made some changes because stock version didn't support microphone.
