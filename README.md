#HW3
<!DOCTYPE html>
<html>

<head>

<meta name="viewport" content="width=device-width, initial-scale=1">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

<title>HW3 Top Oyunu</title>



	<style>
    	

    	canvas#canvas
    		{
    			background: #cfcfcf;
    			display: block;
    			margin: 0 auto;
    			padding: 0;
    			width: 480px;
    			height: 375px;
    			position: absolute;
    			top: 50vh;
    			left: 50vw;
    			transform: translate(-50%,-50%);
    		}
    </style>




</head>

<body>

	<canvas id="canvas"></canvas>

	<script>



		var canvas = document.getElementById("canvas");

		var x = canvas.width/3;
		var y = canvas.height-15;
		var dx = .45;                               
		var dy = -.85;

		var R = 4;

		var atıcıHeight = 3;
		var atıcıWidth = 40;
		var atıcı = (canvas.width-atıcıWidth) / 2;
		var sagPad = false;
		var solPad = false;

		var brickHeight = 10;
		var brickWidth = 50;

		var brickR = [];
		var brickB = [];
		var brickG = [];
		var brickP = [];
		var brickY = [];

				brickR[0] = {durum:1};
				brickB[0] = {durum:1};
				brickG[0] = {durum:1};
				brickP[0] = {durum:1};
				brickY[0] = {durum:1}; 

		var score = 0;

		var renk = "rgba(110, 170, 255, 1)";

		
		var gbl = canvas.getContext("2d");
		gbl.beginPath();
		gbl.rect(110, 70, 55, 4);
		gbl.fillStyle = "black";
		gbl.fill();
		gbl.closePath();

		

		var gball = canvas.getContext("2d");
		gball.beginPath();
		gball.arc(155, 117, R, 0, Math.PI*2,);
		gball.fillStyle = "rgba(110, 170, 255, 1)";
		gball.fill();
		gball.closePath();



		var gstick = canvas.getContext("2d");
		



		

		document.addEventListener("keydown", keyDownHandler, false);
		document.addEventListener("keyup", keyUpHandler, false);
		document.addEventListener("mousemove", mouseMoveHandler, false);

		function mouseMoveHandler(e) 
		{
		    var relativeX = e.clientX - canvas.offsetLeft;
		    if(relativeX > 0 && relativeX < canvas.width) 
			    {
			        atıcı = relativeX - atıcıWidth/2;
	    		}
		}

		function sutunCiz()
			{
				
				if(brickR[0].durum == 1)
					{
						var gr = canvas.getContext("2d");
						gr.beginPath();
						gr.rect(55, 10, brickWidth, brickHeight);
						gr.fillStyle = "red";
						gr.fill();
						gr.closePath();
					}

				if(brickB[0].durum == 1)
					{
						var gb = canvas.getContext("2d");
						gb.beginPath();
						gb.rect(125, 10, brickWidth, brickHeight);
						gb.fillStyle = "blue";
						gb.fill();
						gb.closePath();
					}

				if(brickG[0].durum == 1)
					{	
						var gg = canvas.getContext("2d");
						gg.beginPath();
						gg.rect(195, 10, brickWidth, brickHeight);
						gg.fillStyle = "green";
						gg.fill();
						gg.closePath();
					}
				if(brickP[0].durum == 1)
					{
						var gp = canvas.getContext("2d");
						gp.beginPath();
						gp.rect(95, 30, brickWidth, brickHeight);
						gp.fillStyle = "purple";
						gp.fill();
						gp.closePath();
					}
				if(brickY[0].durum == 1)
					{
						var gy = canvas.getContext("2d");
						gy.beginPath();
						gy.rect(165, 30, brickWidth, brickHeight);
						gy.fillStyle = "yellow";
						gy.fill();
						gy.closePath();
					}
			}

		
		

		function keyDownHandler(e) 
			{
			    if(e.key == "Right" || e.key == "ArrowRight") 
				    {
				        sagPad = true;
				    }
			    else if(e.key == "Left" || e.key == "ArrowLeft") 
				    {
				        solPad = true;
				    }
			}

		function keyUpHandler(e) 
			{
			    if(e.key == "Right" || e.key == "ArrowRight") 
				    {
				        sagPad = false;
				    }
			    else if(e.key == "Left" || e.key == "ArrowLeft") 
				    {
				        solPad = false;
				    }
			}

		function carpısma()
			{
				if(brickR[0].durum == 1)
					{
						if(x > 55.1 - R && x < 55.1+brickWidth + R && y > 10.1 -R && y < 10.1+brickHeight+R) 
							{
			                	dy = -dy;
			                	brickR[0].durum = 0;
			                	renk = "red";
			                	score += 20;
			                	if(score >= 230) 
				                	{
				                        oyunSonu();
	                    			}
			            	}	
					}
				if(brickB[0].durum == 1)
					{
						if(x > 125.1 - R && x < 125.1+brickWidth + R && y > 10.1 -R && y < 10.1+brickHeight+R) 
							{
			                	dy = -dy;
			                	brickB[0].durum = 0;
			                	renk = "blue";
			                	score += 40;
			                	if(score >= 230) 
				                	{
				                        oyunSonu();
	                    			}
			            	}	
					}
				if(brickG[0].durum == 1)
					{
						if(x > 195.1 - R && x < 195.1+brickWidth + R && y > 10.1 -R && y < 10.1+brickHeight+R) 
							{
			                	dy = -dy;
			                	brickG[0].durum = 0;
			                	renk = "green";
			                	score += 80;
			                	if(score >= 230) 
				                	{
				                        oyunSonu();
	                    			}
			            	}	
					}
				if(brickP[0].durum == 1)
					{
						if(x > 95.1 - R && x < 95.1+brickWidth + R && y > 30.1 -R && y < 30.1+brickHeight+R) 
							{
			                	dy = -dy;
			                	brickP[0].durum = 0;
			                	renk = "purple";
			                	score += 60;
			                	if(score >= 230) 
				                	{
				                        oyunSonu();
	                    			}
			            	}	
					}
				if(brickY[0].durum == 1)
					{
						if(x > 165.1 - R && x < 165.1+brickWidth + R && y > 30.1 -R && y < 30.1+brickHeight+R) 
							{
			                	dy = -dy;
			                	brickY[0].durum = 0;
			                	renk = "yellow";
			                	score += 50;
			                	if(score >= 230) 
				                	{
				                        oyunSonu();
				                        
	                    			}
			            	}	
					}

				if(x >= 110.1 - R && x <= 110.1+55 + R && y >= 70.1 -R && y <= 70.1+4+R) 
							{
								if(x < 110.1)
								{
									dx = -dx;
								}

								else if (x > 165.1)
								{
									dx = -dx;
								}
			                	
			                	else
			                	{
			                		dy = -dy;
			                	}

			            	}
			}


		function oyunSonu()
			{
				setTimeout(function()
					{ 
						alert("YOU WIN, CONGRATULATIONS!");
						document.location.reload();
				        clearInterval(dongu); 
					}, 50);
				
			}

		function puanlama()
			{
				var gScore = canvas.getContext('2d');
				gScore.beginPath();
				gScore.font = "8px Arial";
			    gScore.fillStyle = "#0095DD";
			    gScore.fillText("Score: "+score, 6, 10);
			    gScore.closePath();
			
			}

		function sabitCubuk()
			{	
				gbl.beginPath();
				gbl.rect(110, 70, 55, 4);
				gbl.fillStyle = "black";
				gbl.fill();
				gbl.closePath();
			}

		function atıcıCiz() 
			{
			    gstick.beginPath();
			    gstick.rect(atıcı, canvas.height-atıcıHeight, atıcıWidth, atıcıHeight);
			    gstick.fillStyle = "rgba(110, 170, 255, 1)";
			    gstick.fill();
			    gstick.closePath();
			}


		function topCiz() 
			{
			    gball.beginPath();
			    gball.arc(x, y, R, 0, Math.PI*2);
			    gball.fillStyle = renk;
			    gball.fill();
			    gball.closePath();
			}

		function draw() 
		{
			    gball.clearRect(0, 0, canvas.width, canvas.height);
			    topCiz();
			    atıcıCiz();
			    carpısma();
			    puanlama();
			    sabitCubuk();
			    sutunCiz();
			    

			    if(x + dx > canvas.width-R || x + dx < R) 
				    {
	    				dx = -dx;
					}

				if(y + dy < R) 
					{
	    				dy = -dy;
					}

				else if(y + dy > canvas.height-R) 
					if(x > atıcı && x < atıcı + atıcıWidth) 
					{
        				dy = -dy;
    				}
			    else 
			    if(x > atıcı && x < atıcı + atıcıWidth) {
        dy = -dy;
    }
    else {
        alert("GAME OVER");
        document.location.reload();
        clearInterval(dongu);
    }

				if(sagPad && atıcı < canvas.width-atıcıWidth) 
					{
        				atıcı += .75;
    				}
			    else if(solPad && atıcı > 0) 
				    {
				        atıcı -= .75;
				    }

				x += dx;
			    y += dy;
		}
		 var dongu = setInterval(draw, 10);


	</script>

</body>
</html>
