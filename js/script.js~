$(document).ready(function(){
			$( "#div-names" ).show();
			$( "#div-game1" ).hide();
			$( "#div-final-scores" ).hide();
			gameNumber = 1;
			$( "#player1" ).focus();
			if( ! ( $('#player1').val() && $('#player2').val() && $('#player3').val() && $('#player4').val() )){
				$( '#form-names' ).submit(function(){
					event.preventDefault();
					if( ! ( $('#player1').val() && $('#player2').val() && $('#player3').val() && $('#player4').val() )){
						alert('You\'ve not enterred all names!');
					}
					else {
						$( ".dummy" ).focus();
						$( ".dummy" ).blur();
						$( "#div-names" ).animate(
									{ opacity: "0" }, 
									1000,
									"swing",
									function(){
										$( "#div-names" ).hide();
										$( "#div-game1" ).show();
										$( "#input-player1-claimed-score" ).focus();	
									}
								);
						$( '#input-player1-claimed-score' ).focus();
						// Write player names
						for( var i = 1; i <= 4; i++ ){
							$( "#player" + i + "-name" ).html( $( "#player" + i ).val() );
						}
						
						// Hands of Game 1 submitted. Update scores.
						$( "#game1" ).submit(function(){
							event.preventDefault();
							if (typeof enterred === 'undefined') {
								// User has enterred claimed scores.
								
								// Check if scores add upto 13.
								sum = 0
								for( var i = 1; i <= 4; i++ ){
									sum += Number($( "#input-player" + i + "-claimed-score" ).val())
								}
								
								alert( "A " + sum + " score game!" );
									
								game1_claimed_score = [];
								for( var i = 1; i <= 4; i++ ){
									game1_claimed_score[i] = $( "#input-player" + i + "-claimed-score" ).val();
									$( "#player" + i + "-claimed-score" ).html(game1_claimed_score[i]);
									$( "#input-player" + i + "-claimed-score" ).val('');
								}	
								$( "#submit-next1" ).val('Next Game');
								$( '#input-player1-claimed-score' ).focus();
								enterred = 1;
							}
							else {
								// User has enterred actual score.
							
								// Check if scores add upto 13.
								sum = 0
								for( var i = 1; i <= 4; i++ ){
									sum += Number($( "#input-player" + i + "-claimed-score" ).val())
								}
								if( sum != 13 ){
									alert( "Scores dont'add up to 13!" );
									return 0;
								}
								// Calculate scores and all other stuff.
								pClaimed = [];
								pActual = [];
								for( var i = 1; i <= 4; i++ ){
									pClaimed[i] = Number(game1_claimed_score[i]); 
									pActual[i] = Number( $("#input-player" + i + "-claimed-score").val() );
									if ( pActual[i] < pClaimed[i] ) {
										$( "#player" + i + "-total-score" ).html( 0 - pClaimed[i] );
									} else {
										difference = pActual[i] - pClaimed[i];
										currentGameScore = Number( pClaimed[i] + 0.1 * difference );
										newTotalScore = Number( $( "#player" + i + "-total-score" ).html() ) + currentGameScore;
										$( "#player" + i + "-total-score" ).html(newTotalScore);
									}
									// Reset all claimed scores and all inputs.
									$( "#input-player" + i + "-claimed-score" ).val('');
									$( "#player" + i + "-claimed-score" ).html('0');
								}
								// Check if 5 games are already over. 
								if( gameNumber == 5){
									finalScores = Object();
									for( var i = 1; i <= 4; i++ ){
										finalScores[i] = Object();
										finalScores[i]['name'] = $( "#player" + i + "-name" ).html();
										finalScores[i]['score'] = $( "#player" + i + "-total-score" ).html()
									}
									
									for( var i = 1; i <= 4; i++ ){
										$( "#rank" + i ).html( finalScores[i]['name'] + " : " + finalScores[i]['score'] );
									}
									$( "#div-game1" ).hide();
									$( "#div-final-scores" ).show();
									return 0;
								}
								// Remove the 'enterred' variable and shift the focus to the first input, and revalue the submit button.
								delete enterred;
								$( '#input-player1-claimed-score' ).focus();
								$( "#submit-next1" ).val('Submit Claimed Scores');
								gameNumber += 1;
								$( "#game-number" ).html( gameNumber );
							}
						});
					}
				});
			}
		});