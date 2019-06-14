		
# Python version required to run this project is 3.6.8
# List of package and versions requied to run the proc
	spacy==2.1.1
	scikit-learn==0.19.2
	numpy==1.16.2
	scipy==1.2.1
	sklearn-crfsuite==0.3.6
	tensorflow==1.9.0
	rasa-nlu==0.13.8
	rasa-core==0.11.1
	rasa-core-sdk==0.11.0
# Download and link en spacy model
	python -m spacy download en_core_web_lg
	python -m spacy link en_core_web_lg en
# Train NLU model
	''' python nlu_model.py '''
# Train the core Model
	''' python -m rasa_core_sdk.endpoint --actions actions '''
	## Open a new terminal and train the Rasa Core model by running:
				''' python dialogue_management_model.py  '''
				
# We need ngrok setup to tunnel to local server
	Download ngrok from https://dashboard.ngrok.com/get-starte. make sure you Login first.
	Unzip to install via $ unzip /path/to/ngrok.zip (double click on the installer for windows)
	Start the ngrok on port 5004
		''' ngrok http 5004 '''
	
# Google assistant setting
	## Initializing the Google Assistant custom action
		Go to Google actions console and select ‘Add/import project’
		Set the name of your project and pick the language you want your assistant to use. Click ‘Create project’.
		Choose ‘Actions SDK' and copy the project ID
		Click on ‘Decide how your Action is invoked’ from a ‘Quick setup’ pane.
		set a name for google assistant identification
	## Download the Google gactions CLI and place it inside your project directory and run form CMD
		''' gactions init '''
	## A new file actions.json will be initialized
		Configure the file by replacing name and URL(obtained from ngrok)
		
# Deploy your custom Google Assistant skill and enable testing
	gactions update --action_package action.json --project <<PROJECT_ID from SDK>>
	gactions test --action_package action.json --project <<PROJECT_ID from SDK>>
		
# Bot can be tested using simulator or mobile app		
		
	
