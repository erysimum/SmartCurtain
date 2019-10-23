# SmartCurtain

Alexa's voice controlling the curtain movement (up, stop, down) through AWS Lambda.
From developer console, create 3 intents (open curtain, closecurtain, and stop curtain) each intents for curtain up, 
curtain down , and curtain stop movement.

Once the ALexa voice command is fired, it hits the respective intent on hitting_Intent_LambdaFunction.
When the respective intent is triggered, the respective state of curtain is save in a Dynamo Database named 'Curtain Table'.
If it is opencurtain intent, state 0 is saved on database.
If it is closecurtain intent, state 1 is saved on database.
If it is stopcurtain intent, state 2 is saved on database.

Getting the state from database.
In order to pass the state of the curtain movement (0,1,2) to Lambda function, getCurtainStatusFromDB Lambda function is 
created. This Lambda grabs the curtain state(0,1,2) from curtain table.

Later the state (0,1,2), is fetched in Arduino via API https://xg2bxzrcog.execute-api.us-east-1.amazonaws.com/prod

