# Provide TTV functions that can be used in ttv code

## def search(query):
    """
    Return the query object from search query
    A query is a simple search against many different indexes,
    so it is possible that the schema it returns differs.
    For search against many indexes other than sub,
    the searcher will join the result and returns Sub instance.
    Material is another possible return

    Args:
        query (str): query string

    Returns:
        list: A list of Material or Sub object

    >>> resp = search('type=material&filter=tags.keyword%3D%22炫彩背景%22')
    >>> resp.count
    12
    >>> type(resp[0])
    <class 'search.Material'>

    """

## def tag(name, size=5):
    """
    Search the Material database with tag

    Args:
        name (str): The name of the tag. Search the whole tag only
        size (int, optional): How many result. Defaults to 5.

    Returns:
        list: A list of Material object
    """

## def sqrt(number):
    """
    Return square root of the input expression
    >>> sqrt(4.0)
    2.0
    """

## def get_beats(audio):
    """
    Get music beats

    Args:
        audio (str): File location

    Returns:
        array: The array of the beats

    >>> tempo, beats = get_beats(tools.COS_LOCAL + '/jianshuo/beats.mp3')
    >>> tempo
    112.34714673913044
    >>> beats[0]
    0.16253968253968254
    """

## def get_beat(audio):
    """
    Get music beat

    Args:
        audio (str): File location
    
    Returns:
        float: How many seconds between each beat
    """

## def qrcode(data):
    """
    QRCode image generator

    Args:
        data (str): Any data, likely to be URL

    Returns:
        str: Temp file of the QR code image
    """

## def read(filename):
    """
    Read content of file

    >>> read(tools.COS_LOCAL + '/lab/data/face_util/sample_girl.meta.xml')[:10]
    '<?xml vers'
    """

## def media_meta(filename):
    """
    Get media information

    Args:
        filename (str): Filename

    >>> print(media_meta('/mnt/mira-1255830993/jianshuo/beats.mp3'))
    {'width': 0, 'height': 0, 'duration': 71.016}

    >>> print(media_meta('/mnt/mira-1255830993/lab/data/videos/blank.mp4'))
    {'width': 1080, 'height': 1080, 'duration': '3.000000'}

    >>> print(media_meta('/mnt/mira-1255830993/lab/data/images/filenotfound.jpg'))
    {'width': 584, 'height': 584, 'duration': 0}
    """

## def read_excel(filename):
    """
    Read content of Excel

    Args:
        filename (str): The absolute path of Excel

    Returns:
        dict: A dict of all lines of Excel with header as key
    """

## def read_json(url):
    """
    Read JSON from API

    Args:
        url (str): The URL for API
    """

## def translate(text):
    """
    Translate Chinese text to English text

    Args:
        text (str): A string of Chinese text
    
    Returns:
        text (str): A string of English text
    """

## def paste_image(image_file, x, y, width, height, canvas_height=640):
    """
        patch a tile into the canvas using image_file
        crop an area with width and height, at (x, y) position
        and paste it into canvas

        x, y - in rpx, and is the center point of the image
        width, height - in rpx
    """

## def listdir(path):
    """
    List the dir

    Args:
        path (str): The path

    Raises:
        FileNotFoundError: If the path does not exist

    Returns:
        list: A list of files in the current path

    >>> listdir(tools.COS_LOCAL + '/lab')
    ['/mnt/mira-1255830993/lab']

    >>> listdir(tools.COS_LOCAL + '/lab/data/reid/*')
    ['/mnt/mira-1255830993/lab/data/reid/youtu_reid_baseline_lite.onnx']

    >>> listdir('https://cos.mirav.cn/lab/data/reid/*')
    ['/mnt/mira-1255830993/lab/data/reid/youtu_reid_baseline_lite.onnx']

    """

## def slotmachine(text):
    """
    一个帮助函数，用来解析slotmachine的文件格式

    Args:
        text (str): Slot Machine 格式的文件。一般是一个JSON文件

    TODOTODO: Need to take a look. What it is?
    """

## def functions():
    """
    This publishes the functions in this file except this one
    to the Jinja system

    Returns:
        dict: name, function pair

    >>> functions().get('search').__name__
    'search'
    """
